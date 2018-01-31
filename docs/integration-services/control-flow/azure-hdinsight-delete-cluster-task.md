---
title: "Tarea de eliminación de clúster de Azure HDInsight | Microsoft Docs"
ms.custom: 
ms.date: 02/28/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: control-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.afpdelcltask.f1
- sql14.dts.designer.afpdelcltask.f1
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: db580410f37f1310ccc2bf30f6620157fcb60cf9
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="azure-hdinsight-delete-cluster-task"></a>Tarea de eliminación de clúster de HDInsight de Azure
La **tarea de eliminación de clúster de Azure HDInsight** permite que un paquete SSIS elimine un clúster de Azure HDInsight del grupo de recursos y la suscripción de Azure especificados.
  
La **tarea de eliminación de clúster de Azure HDInsight** es un componente de [Feature Pack de SQL Server Integration Services (SSIS) para Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
> [!NOTE]
> La eliminación de un clúster de HDInsight puede tardar entre 10 y 20 minutos.  
  
Para agregar una **tarea de eliminación de clúster de HDInsight de Azure**, arrástrela y suéltela en el Diseñador SSIS y haga doble clic o haga clic con el botón derecho y luego haga clic en **Editar** para ver el siguiente cuadro de diálogo: **Azure HDInsight Delete Cluster Task Editor** (Editor de tareas de eliminación de clúster de HDInsight de Azure).  
  
En la tabla siguiente se proporciona una descripción de los campos del cuadro de diálogo.  
  
|||  
|-|-|  
|**Campo**|**Descripción**|  
|AzureResourceManagerConnection|Seleccione un administrador de conexiones de Azure Resource Manager existente o cree uno nuevo que se usará para eliminar el clúster de HDInsight.|
|SubscriptionId|Especifique el identificador de la suscripción en la que se encuentra el clúster de HDInsight.|
|ResourceGroup|Especifique el grupo de recursos de Azure en el que se encuentra el clúster de HDInsight.|
|nombreDeClúster|Especifique el nombre del clúster que se va a eliminar.|  
|FailIfNotExists|Especifique si la tarea debe generar un error si no existe el clúster.|
