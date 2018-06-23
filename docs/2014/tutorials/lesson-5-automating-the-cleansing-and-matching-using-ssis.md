---
title: 'Lección 5: Automatizar la limpieza y búsqueda de coincidencias con SSIS | Documentos de Microsoft'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f068d4db-2d56-41b1-bed2-0cffa3ca411d
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 00dff9ac204e5e1b86feafc51da643222bce1758
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36104828"
---
# <a name="lesson-5-automating-the-cleansing-and-matching-using-ssis"></a>Lección 5: automatizar la limpieza y la búsqueda de coincidencias con SSIS
  En la lección 1, se genera la base de conocimiento proveedores y usado para limpiar los datos en la lección 2 y coinciden con los datos en la lección 3 mediante la herramienta **cliente DQS**. En un escenario real, quizá deba extraer datos de un origen que no es compatible con DQS o desea automatizar la limpieza y el proceso de coincidencia sin tener que utilizar el **cliente DQS** herramienta. SQL Server Integration Services (SSIS) tiene componentes que puede usar para integrar datos procedentes de diversos orígenes heterogéneos y un **[HYPERLINK "http://msdn.microsoft.com/library/ee677619.aspx" \t "_blank" transformación limpieza de DQS](http://msdn.microsoft.com/library/ee677619.aspx)** componente para invocar la funcionalidad de limpieza expuesta por DQS. Actualmente, DQS no expone la funcionalidad de coincidencia para que la use SSIS, pero puede usar el **[transformación Agrupación aproximada](http://msdn.microsoft.com/library/ms141764.aspx)** para identificar duplicados en los datos.  
  
 Puede cargar datos en MDS mediante la **característica de almacenamiento provisional basado en entidad**. Cuando crea una entidad en MDS, se crean automáticamente las tablas de ensayo y los procedimientos almacenados correspondientes. Por ejemplo, cuando crea la entidad de proveedor, el **stg.supplier_Leaf** tabla y la **stg.udp_Supplier_Leaf** automáticamente se crea el procedimiento almacenado. Use las tablas de ensayo y los procedimientos para crear, actualizar y eliminar miembros de entidad. En esta lección, creará nuevos miembros para la entidad Proveedor. Para cargar datos en el servidor de MDS, el paquete SSIS los carga primero en la tabla de ensayo stg.supplier_Leaf y después desencadena el procedimiento almacenado stg.udp_Supplier_Leaf asociado. Vea [la importación de datos](http://msdn.microsoft.com/library/ee633726.aspx) para obtener más detalles.  
  
 En esta lección, realizará las tareas siguientes:  
  
1.  Quitar datos de proveedor en MDS (si ha realizado las cuatro lecciones anteriores). El paquete SSIS que crea en esta lección carga los datos en MDS automáticamente. Antes, cargaba manualmente los datos de proveedor limpios y coincidentes en el servidor de MDS con el Cliente de DQS.  
  
2.  Crear una vista de suscripciones en la entidad Proveedor para exponer los datos de la entidad en otras aplicaciones. Esta acción crea una vista de SQL que comprobará mediante SQL Server Management Studio. No usará esta vista en esta versión del tutorial.  
  
3.  Crear y ejecutar un proyecto de SSIS mediante **SQL Server Data Tools**. El proyecto utiliza **limpieza de datos** transformación para enviar una solicitud de limpieza en el servidor DQS. DQS no expone la funcionalidad de coincidencia, por lo que se va a usar **agrupación aproximada** transformación para identificar los duplicados.  
  
4.  Comprobar que los datos se crean en MDS mediante Master Data Manager.  
  
5.  Revisar los resultados del proyecto de limpieza de DQS creado por el paquete SSIS y realizar opcionalmente una limpieza interactiva para mejorar la base de conocimiento.  
  
## <a name="next-step"></a>Paso siguiente  
 [Tarea 1 &#40;requisitos previos&#41;: quitar datos de proveedor en MDS](../../2014/tutorials/task-1-prerequisite-removing-supplier-data-in-mds.md)  
  
  