---
title: NO (MDX) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- NOT
dev_langs:
- kbMDX
helpviewer_keywords:
- NOT operator [MDX]
ms.assetid: c11bd3b0-54b3-4a6d-babc-6067722194db
caps.latest.revision: 26
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: b87d48d767414cca4a599b5f883756c02d97ceca
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="not-mdx"></a>NOT (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Realiza una negación lógica de una expresión numérica.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
NOT Expression1  
```  
  
#### <a name="parameters"></a>Parámetros  
 *Expression1*  
 Una expresión MDX (Expresiones multidimensionales) válida que devuelve un valor numérico.  
  
## <a name="return-value"></a>Valor devuelto  
 Un valor booleano que devuelve **false** si el argumento se evalúa como **true**; en caso contrario, **true**.  
  
## <a name="remarks"></a>Comentarios  
 El **no** operador trata la expresión como un valor booleano (cero, 0, como **false**; en caso contrario, **true**) antes de que el operador realice la negación lógica. La tabla siguiente se muestra cómo el **no** operador realiza la negación lógica.  
  
|*Expression1*|Valor devuelto|  
|-------------------|------------------|  
|**true**|**False**|  
|**False**|**true**|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de operadores MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
