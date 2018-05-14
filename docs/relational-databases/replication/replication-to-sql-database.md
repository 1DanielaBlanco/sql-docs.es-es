---
title: Replicación a base de datos SQL | Microsoft Docs
ms.custom: ''
ms.date: 04/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Database replication
- replication, SQL Database
ms.assetid: e8484da7-495f-4dac-b38e-bcdc4691f9fa
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5e3099ebb18883a99b5815b3db3e40f178b22234
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="replication-to-sql-database"></a>Replicación a SQL Database
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  La replicación de[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se puede configurar para [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)].  
 
 ### <a name="supported-configurations"></a>**Configuraciones admitidas:**  
 -  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] puede ser una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que se ejecute en local o una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que se ejecute en una máquina virtual de Azure en la nube. Para obtener más información, consulte [Información general sobre SQL Server en máquinas virtuales de Azure](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/).  
 - [!INCLUDE[ssSDS](../../includes/sssds-md.md)] debe ser un suscriptor de inserción de un publicador de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
 -  No se pueden colocar la base de datos de distribución y los agentes de replicación en [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
 - Se admite la replicación transaccional unidireccional y la de instantáneas. No se admite la replicación transaccional punto a punto ni la de mezcla.  
 
 ## <a name="versions"></a>Versiones  
 - El publicador y el distribuidor deben estar al menos en una de las siguientes versiones:  
   
 -   [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)]  
 
 -   [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
   
 -   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP1 CU3  
   
 -   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] RTM CU10  
   
 -   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 CU8  
   
 -   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] esperado en SP3  
   
 - El intento de configurar la replicación con una versión anterior puede dar lugar a los números de error MSSQL_REPL20084 (El proceso no pudo conectarse a Suscriptor) y MSSQL_REPL40532 (No se puede abrir el servidor \<nombre> solicitado por el inicio de sesión. Error de inicio de sesión).  
 
 - El suscriptor de [!INCLUDE[ssSDS](../../includes/sssds-md.md)] debe ser al menos V12 y puede estar en cualquier región.  
   
 - Para usar todas las características de [!INCLUDE[ssSDS](../../includes/sssds-md.md)], debe usar las versiones más recientes de [SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx) y de [SQL Server Data Tools](https://msdn.microsoft.com/library/mt204009.aspx).  
   
 ## <a name="remarks"></a>Notas  
 - La replicación puede configurarse mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o por medio de la ejecución de instrucciones de [!INCLUDE[tsql](../../includes/tsql-md.md)] en el publicador. No se puede configurar la replicación mediante el portal de [!INCLUDE[ssSDS](../../includes/sssds-md.md)] .  
   
 - La replicación solo puede usar inicios de sesión de autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para conectarse a [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
   
 - La tabla replicada debe tener una clave principal.  
   
 - Debe tener una suscripción de Azure y una [!INCLUDE[ssSDS](../../includes/sssds-md.md)] V12 existente.  
   
 - Una sola publicación en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] puede admitir tanto suscriptores de [!INCLUDE[ssSDS](../../includes/sssds-md.md)] como de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (locales y [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en una máquina virtual de Azure).  
   
 - La administración de replicación, la supervisión y la solución de problemas deben realizarse desde [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]local.  
   
 - Solo se admiten suscripciones de inserción a [!INCLUDE[ssSDS](../../includes/sssds-md.md)] .  
   
 - Solo se admite `@subscriber_type = 0` en **sp_addsubscription** para Base de datos SQL.  
   
 - [!INCLUDE[ssSDS](../../includes/sssds-md.md)] no admite la replicación bidireccional, inmediata, actualizable ni punto a punto.      
   
 ## <a name="replication-architecture"></a>Arquitectura de replicación  
 ![replication-to-sql-database](../../relational-databases/replication/media/replication-to-sql-database.png "replication-to-sql-database")  
   
 ## <a name="scenarios"></a>Escenarios  
   
 ### <a name="typical-replication-scenario"></a>Escenario típico de replicación  
   
 1.  Cree una publicación de replicación transaccional en una base de datos local de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
   
 2.  En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] local, use el **Asistente para nueva suscripción** o instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)] para crear una suscripción de inserción a [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
   
 3.  El conjunto de datos inicial es normalmente una instantánea que se crea con el Agente de instantáneas y se distribuye y aplica a través del Agente de distribución. También se puede suministrar el conjunto de datos inicial mediante una copia de seguridad u otro medio, como [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
   
 #### <a name="data-migration-scenario"></a>Escenario de migración de datos  
   
 1.  Use la replicación transaccional para replicar datos desde una base de datos local de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
   
 2.  Redirija las aplicaciones de cliente o nivel intermedio para actualizar la copia de [!INCLUDE[ssSDS](../../includes/sssds-md.md)] .  
   
 3.  Detenga la actualización de la versión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la tabla y quite la publicación.  
   
 ## <a name="limitations"></a>Limitaciones  
  No se admiten las siguientes opciones para suscripciones de [!INCLUDE[ssSDS](../../includes/sssds-md.md)] :  
   
 -   Copiar asociaciones de grupos de archivos  
   
 -   Copiar esquemas de particionamiento de tabla  
   
 -   Copiar esquemas de particionamiento de índice  
   
 -   Copiar estadísticas definidas por el usuario  
   
 -   Copiar enlaces predeterminados  
   
 -   Copiar enlaces de reglas  
   
 -   Copiar índices de texto  
   
 -   Copiar XML XSD  
   
 -   Copiar índices XML  
   
 -   Copiar permisos  
   
 -   Copiar índices espaciales  
   
 -   Copiar índices filtrados  
   
 -   Copiar atributo de compresión de datos  
   
 -   Copiar atributo de columna dispersa  
   
 -   Convertir tipo de secuencia de archivos a tipos de datos MAX  
   
 -   Convertir tipo hierarchyId a tipos de datos MAX  
   
 -   Convertir tipo espacial a tipos de datos MAX  
   
 -   Copiar propiedades extendidas  
   
 -   Copiar permisos  
   
### <a name="limitations-to-be-determined"></a>Limitaciones para determinar 
 
 -   Copiar intercalación  
   
 -   Ejecución en una transacción serializada de SP  
   
 ## <a name="examples"></a>Ejemplos  
  Cree una publicación y una suscripción de inserción. Para obtener más información, vea:  
   
 -   [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)  
   
 -   [Cree una suscripción de inserción](../../relational-databases/replication/create-a-push-subscription.md) mediante el nombre del servidor lógico de [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] como suscriptor (por ejemplo, **N'azuresqldbdns.database.windows.net'**) y el nombre de [!INCLUDE[ssSDS](../../includes/sssds-md.md)] como base de datos de destino (por ejemplo, **AdventureWorks**).  
   
 ## <a name="see-also"></a>Ver también  
 - [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 - [Crear una suscripción de inserción](../../relational-databases/replication/create-a-push-subscription.md)   
 - [Tipos de replicación](../../relational-databases/replication/types-of-replication.md)   
 - [Monitoring &#40;Replication&#41;](../../relational-databases/replication/monitor/monitoring-replication.md) (Monitorización [replicación])   
 - [Inicializar una suscripción](../../relational-databases/replication/initialize-a-subscription.md)  
