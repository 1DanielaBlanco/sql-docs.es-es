---
title: Elemento de la tabla de esquema (DTA) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Table element [DTA]
ms.assetid: a59e8319-05d1-47f3-af39-7d970ab8e7dc
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7be528ca94c331085aadbb7872d984c80550429a
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MTE
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="table-element-for-schema-dta"></a>Table (DTA, elemento de Schema)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Especifica la tabla que se va a optimizar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
<Schema>  
...code removed here...  
    <Table>...</Table>  
```  
  
## <a name="element-attributes"></a>Atributos del elemento  
  
|Attribute|Description|  
|---------------|-----------------|  
|**NumberOfRows**|Opcional. Entero que permite simular tablas de diferentes tamaños.|  
  
## <a name="element-characteristics"></a>Características del elemento  
  
|Característica|Description|  
|--------------------|-----------------|  
|**Tipo y longitud de los datos**|**string**, entre 1 y 255 caracteres.|  
|**Valor predeterminado**|Ninguno.|  
|**Repetición**|Opcional. Presenta tantas tablas como sea necesario para la carga de trabajo.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elementos|  
|------------------|--------------|  
|**Elemento primario**|[Schema &#40;DTA, elemento de Database&#41;](../../tools/dta/schema-element-for-database-dta.md)|  
|**Elementos secundarios**|[Elemento Name de Table &#40;DTA&#41;](../../tools/dta/name-element-for-table-dta.md)|  
  
## <a name="remarks"></a>Notas  
 Si no se especifica un elemento **Table** , el Asistente para la optimización de motor de base de datos asumirá que todas las tablas de la base de datos especificada se pueden optimizar.  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo de uso, vea [Server &#40;DTA, elemento&#41;](../../tools/dta/server-element-dta.md).  
  
## <a name="see-also"></a>Ver también  
 [Referencia del archivo de entrada XML &#40;Asistente para la optimización de motor de base de datos&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
