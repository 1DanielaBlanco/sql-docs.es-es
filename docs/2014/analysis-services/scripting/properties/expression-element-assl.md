---
title: Elemento Expression (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Expression Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Expression
helpviewer_keywords:
- Expression element
ms.assetid: a9491b21-5279-4531-b6a5-9e8022060dd8
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3d7ba9bbfeddef0d4d7466141cabb914f4289034
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155327"
---
# <a name="expression-element-assl"></a>Elemento Expression (ASSL)
  Contiene una expresión MDX (Expresiones multidimensionales) que define el contenido del elemento primario.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<CellPermission> <!-- or StandardAction -->  
   ...  
   <Expression>...</Expression>  
   ...  
</CellPermission>  
```  
  
## <a name="element-characteristics"></a>Características del elemento  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|String|  
|Valor predeterminado|None|  
|Cardinalidad|1-1: Elemento necesario que se produce una vez y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[CellPermission](../objects/cellpermission-element-assl.md), [StandardAction](../data-type/action-data-type-assl.md)|  
|Elementos secundarios|None|  
  
## <a name="remarks"></a>Notas  
 Para el `CellPermission` elemento, el `Expression` elemento contiene una expresión MDX lógica que identifica las celdas aplicables a los derechos indicados por el [acceso](access-element-assl.md) elemento de la `CellPermission` elemento. Si el valor de un elemento `Expression` para un elemento `CellPermission` está vacío, se omite el elemento `CellPermission`.  
  
 Para el elemento `StandardAction`, el elemento `Expression` contiene una expresión MDX que representa el contenido de la acción. Si el valor de un elemento `Expression` para un elemento `StandardAction` está vacío, se omite el elemento `StandardAction`.  
  
 Los elementos que corresponden a los elementos primarios en el modelo de objetos Objetos de administración de análisis (AMO) son <xref:Microsoft.AnalysisServices.CellPermission> y <xref:Microsoft.AnalysisServices.StandardAction>.  
  
## <a name="see-also"></a>Vea también  
 [Propiedades &#40;ASSL&#41;](properties-assl.md)  
  
  
