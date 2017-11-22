---
title: Crear la base de datos de almacenamiento provisional para almacenamiento de datos paralelos
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.suite: sql
ms.custom: 
ms.technology: mpp-data-warehouse
description: Almacenamiento de datos paralelos (PDW) de SQL Server utiliza una base de datos de almacenamiento provisional para almacenar datos temporalmente durante el proceso de carga.
ms.date: 10/20/2016
ms.topic: article
ms.assetid: 6d0b2726-4772-4858-b700-885cc12219b2
caps.latest.revision: "20"
ms.openlocfilehash: f88e2c45aaed8b6f2b3bfb6fe610a0f228c4449e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="staging-database"></a>Base de datos de almacenamiento provisional 
Almacenamiento de datos paralelos (PDW) de SQL Server utiliza una base de datos de almacenamiento provisional para almacenar datos temporalmente durante el proceso de carga. De forma predeterminada, SQL Server PDW utiliza la base de datos de destino como la base de datos de almacenamiento provisional que puede provocar la fragmentación de las tablas. Para reducir la fragmentación de las tablas, puede crear una base de datos de almacenamiento provisional definido por el usuario. O bien, cuando la reversión de un error de carga no es un problema, puede usar el modo de carga de fastappend para mejorar el rendimiento mediante la omisión de la tabla temporal y cargando directamente en la tabla de destino.  
  
## <a name="StagingDatabase"></a>Conceptos básicos de la base de datos de almacenamiento provisional  
A *base de datos provisional* creados por el usuario PDW base de datos que almacena los datos temporalmente mientras se está cargando en el dispositivo. Cuando se especifica una base de datos de almacenamiento provisional para una carga, el dispositivo primero copia los datos en la base de datos provisional y, a continuación, copia los datos de tablas temporales en la base de datos de ensayo en tablas permanentes en la base de datos de destino.  
  
Cuando una base de datos de almacenamiento provisional no se especifica para una carga, SQL ServerPDW crea las tablas temporales en la base de datos de destino y los utiliza para almacenar los datos cargados antes de insertar los datos cargados en las tablas de destino permanente.  
  
Cuando se utiliza una carga el *fastappend modo*, ServerPDW de SQL omite la utilizan tablas temporales por completo y anexa los datos directamente a la tabla de destino. El modo de fastappend mejora el rendimiento de carga para los escenarios de ETL que se cargan datos en una tabla que es una tabla temporal desde la perspectiva de aplicaciones. Por ejemplo, un proceso ETL pudo cargar datos en una tabla temporal, procesar los datos de limpieza y deduplicación anular y, a continuación, inserte los datos en la tabla de hechos de destino. En este caso, no es necesario para PDW primera carga los datos en una tabla temporal interna antes de insertar los datos en la tabla temporal de la aplicación. El modo de fastappend evita el paso de la carga adicional, lo que mejora notablemente el rendimiento de carga. Tenga en cuenta que para utilizar el modo de fastappend, debe utilizar el modo de transacción múltiple, lo que significa que la recuperación de una carga anulada o con error deberá controlarse mediante su propio proceso de carga.  
  
**Ventajas de la base de datos de almacenamiento provisional**  
  
Es la principal ventaja de una base de datos de almacenamiento provisional reducir la fragmentación de las tablas. Si no se utiliza una base de datos de almacenamiento provisional, los datos se cargan en tablas temporales de la base de datos de destino. Al obtengan crea tablas temporales y se coloca en la base de datos de destino, las páginas de las tablas temporales y tablas permanentes se convierten en intercalada. Con el tiempo, esto produce la fragmentación de tabla y degrada el rendimiento. En cambio, una base de datos de almacenamiento provisional garantiza que las tablas temporales se crean y quitan en un espacio de archivo independiente de las tablas permanentes.  
  
**Estructuras de tabla de base de datos de almacenamiento provisional**  
  
La estructura de almacenamiento para cada tabla de base de datos depende de la tabla de destino.  
  
-   Para las cargas en un montón o índice de almacén de columnas agrupado, la tabla de ensayo es un montón.  
  
-   Para las cargas en un índice agrupado de almacén de filas, la tabla de ensayo es un índice agrupado de almacén.  
  
## <a name="Permissions"></a>Permissions  
Requiere permiso de creación (para crear una tabla temporal) en la base de datos de almacenamiento provisional. 

<!-- MISSING LINKS

For more information, see [Grant Permissions to load data](grant-permissions-to-load-data.md).  

-->
  
## <a name="CreatingStagingDatabase"></a>Procedimientos recomendados para crear una base de datos provisional  
  
1.  Solo debe haber una base de datos de almacenamiento provisional por dispositivo. Esto se puede compartir con todos los trabajos de carga de todas las bases de datos de destino.  
  
2.  El tamaño de la base de datos de almacenamiento provisional es específica del cliente. Inicialmente, al rellenar primero el dispositivo, la base de datos de almacenamiento provisional debe ser lo suficientemente grande como para dar cabida a los trabajos de carga inicial. Cargar los trabajos tienden a ser grandes porque pueden se producen varias cargas al mismo tiempo. Una vez han completado los trabajos de carga inicial y el sistema está en producción, el tamaño de cada trabajo de carga es probable que sea menor. Cuando esto ocurre, puede reducir el tamaño de la base de datos de almacenamiento provisional para dar cabida a los tamaños de carga más pequeños. Para reducir el tamaño, puede quitar la base de datos provisional y vuelva a crearlo con una asignación menor tamaño, o puede usar el [ALTER DATABASE](../t-sql/statements/alter-database-parallel-data-warehouse.md) instrucción.  
  
    Al crear la base de datos de almacenamiento provisional, utilice las instrucciones siguientes.  
  
    -   El tamaño de la tabla replicada debe ser el tamaño estimado por nodo de proceso, de todas las tablas replicadas se cargará de forma simultánea. Por lo general, suele ser 25-30 GB.  
  
    -   El tamaño de la tabla distribuida debe tener el tamaño estimado, por dispositivo, de todas las tablas distribuidas que se cargará al mismo tiempo.  
  
    -   El tamaño del registro es normalmente similar al tamaño de la tabla replicada.  
  
## <a name="Examples"></a>Ejemplos  
  
### <a name="a-create-a-staging-database"></a>A. Crear una base de datos provisional 
En el ejemplo siguiente se crea una base de datos provisional, Stagedb, para su uso con todas las cargas en el dispositivo. Imagine que estime que replican cinco tablas del tamaño de 5 GB se cargará al mismo tiempo. Esto da como resultado en la asignación de al menos 25 GB para el tamaño replicado. Imagine que calculan que distribuyen seis tablas de tamaños de 100, 200, 400, 500, 500 y 550 GB se cargarán al mismo tiempo. Esto da como resultado asignar 2250 GB como mínimo para el tamaño de la tabla distribuida.  
  
```sql  
CREATE DATABASE Stagedb  
WITH (  
  
    AUTOGROW = ON,  
  
    REPLICATED_SIZE = 25 GB,  
  
    DISTRIBUTED_SIZE = 2250 GB,  
  
    LOG_SIZE = 25 GB  
  
);  
```  

<!-- MISSING LINKS
 
## See Also  
[Common metadata query examples](metadata-query-examples.md)  

-->
  
