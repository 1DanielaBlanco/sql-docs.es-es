---
title: El nombre de elemento de tabla (DTA) | Documentos de Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: dta
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: Name element
ms.assetid: 422a755f-ee52-4863-b1aa-f4ef1b8fd0bb
caps.latest.revision: "12"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 38938f788b00e41acf726acb2af6cf275668e39d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="name-element-for-table-dta"></a>Name (DTA, elemento de Table)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Especifica un nombre de tabla para la optimización.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
<Schema>  
    <Table>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a>Características del elemento  
  
|Característica|Description|  
|--------------------|-----------------|  
|**Tipo y longitud de los datos**|**string**, entre 1 y 255 caracteres.|  
|**Valor predeterminado**|Ninguno.|  
|**Repetición**|Requerido. Una por cada elemento **Table** .|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elementos|  
|------------------|--------------|  
|**Elemento primario**|[Table &#40;DTA, elemento de Schema&#41;](../../tools/dta/table-element-for-schema-dta.md)|  
|**Elementos secundarios**|Ninguno.|  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo de uso, vea [Server &#40;DTA, elemento&#41;](../../tools/dta/server-element-dta.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia del archivo de entrada XML &#40;Asistente para la optimización de motor de base de datos&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
