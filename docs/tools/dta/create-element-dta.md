---
title: Crear el elemento (DTA) | Documentos de Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Create element (DTA)
ms.assetid: 9d076c90-f933-45f4-b6d9-447793f6528b
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 36d80fd25c31641b693370d9a4212a8454981878
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="create-element-dta"></a>Create (DTA, elemento)
  Contiene información sobre los índices, las estadísticas o las estructuras de montones de una configuración especificada por el usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
<Recommendation>  
    <Create>  
    ...code removed here...  
    </Create>  
</Recommendation>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|**Tipo y longitud de los datos**|Ninguno.|  
|**Valor predeterminado**|Ninguno.|  
|**Repetición**|Una obligatoria por cada tipo de estructura de diseño físico (índices, estadísticas o estructuras de montones).|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elementos|  
|------------------|--------------|  
|**Elemento primario**|[Elemento Recommendation &#40; DTA &#41;](../../tools/dta/recommendation-element-dta.md)|  
|**Elementos secundarios**|[Index &#40;DTA, elemento&#41;](../../tools/dta/index-element-dta.md)<br /><br /> Elemento**Statistics** (para obtener más información, vea el [esquema XML del Asistente para la optimización de motor de base de datos](http://schemas.microsoft.com/sqlserver/) ).<br /><br /> Elemento**Heap** (para obtener más información, vea el [esquema XML del Asistente para la optimización de motor de base de datos](http://schemas.microsoft.com/sqlserver/) ).|  
  
## <a name="remarks"></a>Comentarios  
 Este elemento tiene el nombre **CreateTypecomplexType** en el esquema XML del Asistente para la optimización de motor de base de datos. Se utiliza para crear los índices, las estadísticas y las estructuras de montones de una configuración especificada por el usuario. No confunda este elemento **Create** con los otros tipos que se pueden usar para crear vistas (**CreateViewType**) o particiones (**CreatePType**). Vea el [esquema XML del Asistente para la optimización de motor de base de datos](http://schemas.microsoft.com/sqlserver/) para obtener más información sobre estos otros tipos de elementos **Create** .  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo de uso de este elemento, vea [Ejemplo de archivo de entrada XML con configuración especificada por el usuario &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia del archivo de entrada XML &#40;Asistente para la optimización de motor de base de datos&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  

