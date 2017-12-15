---
title: "Características de Integration Services compatibles con las ediciones de SQL Server| Microsoft Docs"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5018225-68bb-4f34-ae4a-ead79d8ad13a
caps.latest.revision: "15"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 9d7a5ad6abf892a9b8ab0b125336e13cf1318100
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2017
---
# <a name="integration-services-features-supported-by-the-editions-of-sql-server"></a>Características de Integration Services compatibles con las ediciones de SQL Server
 En este tema, encontrará información detallada sobre las características de SQL Server Integration Services (SSIS) admitidas por las diversas ediciones de [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)].  

Para obtener las características compatibles con las ediciones Developer y Evaluation, consulte las características enumeradas para Enterprise Edition en las tablas siguientes.
  
Para consultar las notas de la versión más reciente e información sobre las novedades, consulte los artículos siguientes:
-   [Notas de la versión de SQL Server 2016](../sql-server/sql-server-2016-release-notes.md)
-   [Novedades de Integration Services en SQL Server 2016](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md)
-   [Novedades de Integration Services en SQL Server 2017](../integration-services/what-s-new-in-integration-services-in-sql-server-2017.md)
    
**Pruebe SQL Server 2016.**    

La edición de evaluación de SQL Server está disponible durante un período de prueba de 180 días.  
    
> [![Descargar desde el centro de evaluación](../analysis-services/media/download.png)](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) **[Descargar SQL Server 2016 desde el centro de evaluación](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)**    
    
## <a name="ISNew"></a> Nuevas características de Integration Services en SQL Server 2017
  
|Característica|Enterprise|Standard|Web|Express con Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Patrón de escalabilidad horizontal|Sí|||||
|Trabajo de escalabilidad horizontal|Sí|Sí <sup>1</sup>|TBD|TBD|TBD|
|Compatibilidad con Microsoft Dynamics AX y Microsoft Dynamics CRM en componentes de OData <sup>2</sup>|Sí|Sí||||

<sup>1</sup> Si ejecuta paquetes que solo requieren características de la versión Enterprise en la escalabilidad horizontal, los trabajos de escalabilidad horizontal también deben ejecutarse en instancias de SQL Server Enterprise.

<sup>2</sup> Esta característica también se admite en SQL Server 2016 con Service Pack 1.

## <a name="IEWiz"></a> Asistente para importación y exportación de SQL Server

|Característica|Enterprise|Standard|Web|Express con Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Asistente para importación y exportación de SQL Server|Sí|Sí|Sí|Sí|Sí|  

## <a name="IS"></a> Integration Services  
  
|Característica|Enterprise|Standard|Web|Express con Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Conectores de origen de datos integrados|Sí|Sí|||| 
|Tareas y transformaciones integradas|Sí|Sí||||  
|Origen y destino ODBC de Attunity|Sí|Sí|||| 
|Tareas y conectores de origen de datos de Azure|Sí|Sí||||  
|Conectores y tareas de Hadoop/HDFS|Sí|Sí||||  
|Herramientas de generación de perfiles de datos básicos|Sí|Sí|||| 

## <a name="ISAA"></a> Integration Services: orígenes y destinos avanzados  
  
|Característica|Enterprise|Standard|Web|Express con Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Origen y de destino de Oracle de alto rendimiento de Attunity|Sí|||||  
|Origen y de destino de Teradata de alto rendimiento de Attunity|Sí|||||  
|Origen y destino de SAP BW|Sí|||||  
|Destino de entrenamiento del modelo de minería de datos|Sí|||||  
|Destino de procesamiento de dimensiones|Sí|||||  
|Destino de procesamiento de particiones|Sí|||||  
  
## <a name="ISAT"></a> Integration Services: transformaciones y tareas avanzadas  
  
|Característica|Enterprise|Standard|Web|Express con Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Componentes de Change Data Capture de Attunity <sup>1</sup>|Sí|||||  
|Transformación de consulta de minería de datos|Sí|||||  
|Transformaciones de búsqueda y agrupación aproximadas|Sí|||||  
|Transformaciones de extracción y búsqueda de términos|Sí|||||  

<sup>1</sup> Los componentes de Change Data Capture de Attunity necesitan la edición Enterprise. Sin embargo, Change Data Capture Service y Change Data Capture Designer no necesitan la edición Enterprise. Puede usar el diseñador y el servicio en un equipo donde SSIS no esté instalado.
