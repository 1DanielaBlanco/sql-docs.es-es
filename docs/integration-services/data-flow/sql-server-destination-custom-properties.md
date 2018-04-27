---
title: Propiedades personalizadas del destino SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: data-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b736aa6d-c154-44a0-be08-f25733fca1d9
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 75bdf710a6f6ab62041e29924525dc74fbcd5993
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="sql-server-destination-custom-properties"></a>Propiedades personalizadas del destino SQL Server
  El destino de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tiene propiedades personalizadas y propiedades comunes a todos los componentes de flujo de datos.  
  
 En la tabla siguiente se describen las propiedades personalizadas del destino [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Todas las propiedades son de lectura y escritura.  
  
|Nombre de propiedad|Tipo de datos|Description|  
|-------------------|---------------|-----------------|  
|AlwaysUseDefaultCodePage|Boolean|Obliga a usar el valor de la propiedad DefaultCodePage. El valor predeterminado de esta propiedad es **False**.|  
|BulkInsertCheckConstraints|Boolean|Valor que especifica si la inserción masiva comprueba las restricciones. El valor predeterminado de esta propiedad es **True**.|  
|BulkInsertFireTriggers|Boolean|Valor que especifica si la inserción masiva activa desencadenadores en las tablas. El valor predeterminado de esta propiedad es **False**.|  
|BulkInsertFirstRow|Integer|Valor que especifica la primera fila que insertar. El valor predeterminado de esta propiedad es **-1**, lo que indica que no se ha asignado ningún valor.|  
|BulkInsertKeepIdentity|Boolean|Valor que especifica si los valores se pueden insertar en las columnas de identidad. El valor predeterminado de esta propiedad es **False**.|  
|BulkInsertKeepNulls|Boolean|Valor que especifica si la inserción masiva mantiene los valores Null. El valor predeterminado de esta propiedad es **False**.|  
|BulkInsertLastRow|Integer|Valor que especifica la última fila que insertar. El valor predeterminado de esta propiedad es **-1**, lo que indica que no se ha asignado ningún valor.|  
|BulkInsertMaxErrors|Integer|Valor que especifica el número de errores que se pueden producir antes de que se detenga la inserción masiva. El valor predeterminado de esta propiedad es **-1**, lo que indica que no se ha asignado ningún valor.|  
|BulkInsertOrder|String|Nombres de las columnas de orden. Las columnas se pueden ordenar en sentido ascendente o descendente. Si se utilizan varias columnas de orden, los nombres de columna están separados por comas.|  
|BulkInsertTableName|String|Tabla o vista de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en la base de datos a la que se copian los datos.|  
|BulkInsertTablock|Boolean|Valor que especifica si la tabla se bloquea durante la inserción masiva. El valor predeterminado de esta propiedad es **True**.|  
|DefaultCodePage|Integer|Página de códigos que se usa cuando no hay información disponible de la misma en el origen de datos.|  
|MaxInsertCommitSize|Integer|Valor que especifica el número máximo de filas que insertar en un lote. Cuando el valor es cero, todas las filas se insertan en un único lote.|  
|Timeout|Integer|Valor que especifica el número de segundos que el destino [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] espera antes de la terminación si no hay ningún dato disponible para la inserción. El valor 0 significa que el destino [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no agotará el tiempo de espera. El valor predeterminado de esta propiedad es 30.|  
  
 La entrada y las columnas de entrada del destino [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no tienen ninguna propiedad personalizada.  
  
 Para más información, consulte [SQL Server Destination](../../integration-services/data-flow/sql-server-destination.md).  
  
## <a name="see-also"></a>Ver también  
 [Common Properties](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
