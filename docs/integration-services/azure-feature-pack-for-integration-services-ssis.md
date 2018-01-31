---
title: Azure Feature Pack para Integration Services (SSIS) | Microsoft Docs
ms.custom: 
ms.date: 08/22/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.SSIS.AZURE.F1
- SQL14.SSIS.AZURE.F1
ms.assetid: 31de555f-ae62-4f2f-a6a6-77fea1fa8189
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b05c3b5f768abc35f7a374376a5cb89012f68337
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="azure-feature-pack-for-integration-services-ssis"></a>Azure Feature Pack para Integration Services (SSIS)
Feature Pack de SQL Server Integration Services (SSIS) para Azure es una extensión que proporciona los componentes que se muestran en esta página para que SSIS se conecte a los servicios de Azure, para transferir datos entre Azure y orígenes de datos locales, y para procesar los datos almacenados en Azure.

[![Descargar Feature Pack de SSIS para Azure](../analysis-services/media/download.png)](https://www.microsoft.com/download/details.aspx?id=54798) **Descargar**

- Para SQL Server 2017 - [Feature Pack de Microsoft SQL Server 2017 Integration Services para Azure](https://www.microsoft.com/download/details.aspx?id=54798)
- Para SQL Server 2016 - [Feature Pack de Microsoft SQL Server 2016 Integration Services para Azure](https://www.microsoft.com/download/details.aspx?id=49492)
- Para SQL Server 2014 - [Feature Pack de Microsoft SQL Server 2014 Integration Services para Azure](https://www.microsoft.com/download/details.aspx?id=47366)
- Para SQL Server 2012 - [Feature Pack de Microsoft SQL Server 2012 Integration Services para Azure](https://www.microsoft.com/download/details.aspx?id=47367)

## <a name="components-in-the-feature-pack"></a>Componentes de Feature Pack
-   Administradores de conexión

    -   [Administrador de conexiones de almacenamiento de Azure](../integration-services/connection-manager/azure-storage-connection-manager.md)

    -   [Administrador de conexiones de suscripciones de Azure](../integration-services/connection-manager/azure-subscription-connection-manager.md)
    
    -   [Administrador de conexiones de Azure Data Lake Store](../integration-services/connection-manager/azure-data-lake-store-connection-manager.md)
    
    -   [Administrador de conexiones de Azure Resource Manager](../integration-services/connection-manager/azure-resource-manager-connection-manager.md)
    
    -   [Administrador de conexiones de Azure HDInsight](../integration-services/connection-manager/azure-hdinsight-connection-manager.md)

-   Tareas

    -   [Tarea de carga de blobs de Azure](../integration-services/control-flow/azure-blob-upload-task.md)

    -   [Tarea de descarga de blobs de Azure](../integration-services/control-flow/azure-blob-download-task.md)

    -   [Tarea de Hive de HDInsight de Azure](../integration-services/control-flow/azure-hdinsight-hive-task.md)

    -   [Tarea de Pig de Azure HDInsight](../integration-services/control-flow/azure-hdinsight-pig-task.md)

    -   [Tarea de creación de clúster de HDInsight de Azure](../integration-services/control-flow/azure-hdinsight-create-cluster-task.md)

    -   [Tarea de eliminación de clúster de HDInsight de Azure](../integration-services/control-flow/azure-hdinsight-delete-cluster-task.md)
    
    -   [Tarea de carga de Azure SQL DW](../integration-services/control-flow/azure-sql-dw-upload-task.md)

    -   [Tarea Sistema de archivos de Azure Data Lake Store](../integration-services/control-flow/azure-data-lake-store-file-system-task.md)

-   Componentes de flujo de datos

    -   [Origen de blobs de Azure](../integration-services/data-flow/azure-blob-source.md)

    -   [Destino de blobs de Azure](../integration-services/data-flow/azure-blob-destination.md)
    
    -   [Origen de Azure Data Lake Store](../integration-services/data-flow/azure-data-lake-store-source.md)
    
    -   [Destino de Azure Data Lake Store](../integration-services/data-flow/azure-data-lake-store-destination.md)

-   Blob de Azure y enumerador de archivos ADLS. Consultar [Contenedor de bucles Para cada uno](http://msdn.microsoft.com/library/95a19dde-61ca-4d9b-aa3d-131fa4264296)

## <a name="download-the-feature-pack"></a>Descarga del Feature Pack
 Descargue Feature Pack de SQL Server Integration Services (SSIS) para Azure.
 
- [Feature Pack de SSIS para Azure](http://go.microsoft.com/fwlink/?LinkID=626967) para SQL Server 2016
- [Feature Pack de SSIS para Azure](https://www.microsoft.com/download/details.aspx?id=54798) para [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]

## <a name="prerequisites"></a>Prerequisites
 Necesita instalar los siguientes requisitos previos antes de instalar este Feature Pack.

-   SQL Server Integration Services
-   .Net Framework 4.5

## <a name="scenario-processing-big-data"></a>Escenario: Procesamiento de macrodatos
 Use el Conector Azure para completar el trabajo de procesamiento de macrodatos siguiente:

1.  Utilice la tarea de carga de blobs de Azure para cargar datos de entrada en el almacenamiento de blobs de Azure.

2.  Utilice la tarea de creación de clúster de HDInsight de Azure para crear un clúster de HDInsight de Azure. Este paso es opcional si quiere utilizar su propio clúster.

3.  Utilice la tarea de Hive de HDInsight de Azure o la tarea de Pig de HDInsight de Azure para invocar un trabajo de Pig o Hive en el clúster de HDInsight de Azure.

4.  Utilice la tarea de eliminación de clúster de HDInsight de Azure para eliminar el clúster de HDInsight tras su uso si creó un clúster de HDInsight a petición en el paso 2.

5.  Utilice la tarea de descarga de blobs de HDInsight de Azure para descargar los datos de salida de Pig o Hive del almacenamiento de blobs de Azure.

![SSIS-AzureConnector-BigDataScenario](../integration-services/media/ssis-azureconnector-bigdatascenario.png)
 
## <a name="scenario-managing-data-in-the-cloud"></a>Escenario: Administración de datos en la nube
 Use el destino de blobs de Azure en un paquete de SSIS para escribir los datos de salida en Almacenamiento de blobs de Azure o para utilizar el origen de blobs de Azure para leer datos desde un Almacenamiento de blobs de Azure.

![SSIS-AzureConnector-CloudArchive-1](../integration-services/media/ssis-azureconnector-cloudarchive-1.png)
 
 ![SSIS-AzureConnector-CloudArchive-2](../integration-services/media/ssis-azureconnector-cloudarchive-2.png)

 Utilice el contenedor de bucles Foreach con el enumerador de blobs de Azure para procesar los datos de varios archivos de blob.

![SSIS-AzureConnector-CloudArchive-3](../integration-services/media/ssis-azureconnector-cloudarchive-3.png)
  
