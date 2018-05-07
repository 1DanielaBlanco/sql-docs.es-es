---
title: Operadores unarios | Documentos de Microsoft
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
dev_langs:
- kbMDX
helpviewer_keywords:
- unary operators
ms.assetid: bf1b5518-6040-4484-9ce8-79c0eb4373a9
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 4ee37e10238e0c06b72ae4b188ffbbc740be8335
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="unary-operators"></a>Operadores unarios
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  En las expresiones multidimensionales (MDX), los operadores unarios realizan una operación en un solo operando, como devolver el valor positivo o negativo de una expresión numérica.  
  
 MDX es compatible con los operadores unarios que se indican en la siguiente tabla.  
  
|Operador|Description|  
|--------------|-----------------|  
|[- (Negativo)](../mdx/negative-mdx.md)|Devuelve el valor negativo de una expresión numérica.|  
|[+ (Positivo)](../mdx/positive-mdx.md)|Devuelve el valor positivo de una expresión numérica.|  
  
 En el siguiente ejemplo se ilustra el uso de un operador unario para devolver el valor negativo de una medida:  
  
```  
WITH   
   MEMBER [Measures].[NegDiscountAmount] AS  
   -[Measures].[Discount Amount]  
SELECT   
   {[Measures].[Discount Amount],[Measures].[NegDiscountAmount]} on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
```  
  
 Además, MDX utiliza operadores unarios especiales para determinar la operación de agregación realizada por el [RollupChildren](../mdx/rollupchildren-mdx.md) función. Para obtener más información sobre estos operadores unarios especiales, consulte [agregar una agregación personalizada a una dimensión](../analysis-services/multidimensional-models/bi-wizard-add-a-custom-aggregation-to-a-dimension.md).  
  
## <a name="see-also"></a>Vea también  
 [Operadores &#40;sintaxis MDX&#41;](../mdx/operators-mdx-syntax.md)  
  
  
