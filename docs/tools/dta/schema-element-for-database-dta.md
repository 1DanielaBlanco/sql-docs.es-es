---
title: Elemento de esquema de base de datos (DTA) | Documentos de Microsoft
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
helpviewer_keywords: Schema element
ms.assetid: d932e59c-953f-4ab4-934d-b6baf344835c
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 89c36f9df5ab507edad6254e6c09ccb8039878df
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="schema-element-for-database-dta"></a>Schema (DTA, elemento de Database)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Especifica el esquema de la base de datos que desea optimizar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
<Database>  
...code removed here...  
    <Schema>...</Schema>  
```  
  
## <a name="element-characteristics"></a>Características del elemento  
  
|Característica|Description|  
|--------------------|-----------------|  
|**Tipo y longitud de los datos**|Ninguno.|  
|**Valor predeterminado**|Ninguno.|  
|**Repetición**|Una obligatoria para el elemento **Database** especificado en el elemento **Server** .|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elementos|  
|------------------|--------------|  
|**Elemento primario**|[Elemento Database para servidor &#40;DTA&#41;](../../tools/dta/database-element-for-server-dta.md)|  
|**Elementos secundarios**|[Name &#40;DTA, elemento de Schema&#41;](../../tools/dta/name-element-for-schema-dta.md)<br /><br /> [Table &#40;DTA, elemento de Schema&#41;](../../tools/dta/table-element-for-schema-dta.md)|  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo del uso de este elemento, vea [Elemento Server &#40;DTA&#41;](../../tools/dta/server-element-dta.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia del archivo de entrada XML &#40;Asistente para la optimización de motor de base de datos&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
