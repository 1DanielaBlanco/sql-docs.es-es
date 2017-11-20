---
title: Origen de archivo HDFS | Documentos de Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ssis.designer.hdfsfilesrc.f1
ms.assetid: f8cda200-c389-4a2e-8ee9-5d59b326aac1
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2b7ed3c3789b7c28476719422f600106a73bfebd
ms.contentlocale: es-es
ms.lasthandoff: 08/03/2017

---
# <a name="hdfs-file-source"></a>Origen de archivo HDFS
  El componente de origen de archivo HDFS permite que un paquete SSIS lea datos desde un archivo HDFS. Los formatos de archivo admitidos son Text y Avro. (No se admiten los orígenes ORC).  
  
 Para configurar el componente de origen de archivo HDFS, arrastre y suelte el origen de archivo HDFS en el diseñador de flujo de datos y haga doble clic en el componente para abrir el editor.  
  
 ![Editor de origen de archivo HDFS](../../integration-services/data-flow/media/hdfs-file-source.png "Editor de origen de archivo HDFS")  
  
## <a name="options"></a>Opciones  
 Configure las opciones siguientes en la pestaña **General** del cuadro de diálogo **Hadoop File Source Editor** (Editor de origen de archivo Hadoop).  
  
|Campo|Description|  
|-----------|-----------------|  
|**Hadoop Connection (Conexión de Hadoop)**|Especifique un administrador de conexiones de Hadoop existente o cree uno nuevo. Este administrador de conexiones indica dónde se hospedan los archivos HDFS.|  
|**Ruta del archivo**|Especifique el nombre del archivo HDFS.|  
|**Formato de archivo**|Especifique el formato del archivo HDFS. Las opciones disponibles son Text y Avro. (No se admiten los orígenes ORC).|  
|**Carácter delimitador de columna**|Si selecciona el formato Text, especifique el carácter delimitador de columna.|  
|**Nombres de columna de la primera fila de datos**|Si selecciona el formato Text, indique si la primera fila del archivo contiene nombres de columnas.|  
  
 Después de configurar estas opciones, seleccione la pestaña **Columna** para asignar columnas de origen a columnas de destino del flujo de datos.  
  
## <a name="see-also"></a>Vea también  
 [Administrador de conexiones de Hadoop](../../integration-services/connection-manager/hadoop-connection-manager.md)   
 [Destino de archivo HDFS](../../integration-services/data-flow/hdfs-file-destination.md)  
  
  

