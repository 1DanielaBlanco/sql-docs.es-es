---
title: Predecir (MDX) | Documentos de Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: PREDICT
dev_langs: kbMDX
helpviewer_keywords: Predict function
ms.assetid: a82f3edd-249b-4559-98d3-6e10d81a095d
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: feeadc92c9b30013f3e45e54a7b6464cf0743442
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2017
---
# <a name="predict-mdx"></a>Predict (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

    
> [!CAUTION]  
>  Esta función está en proceso de eliminación debido a incoherencias internas.  
>   
>  Revise la sección de ejemplo para encontrar una solución alternativa mediante una expresión DMX.  
  
 Devuelve un valor de una expresión numérica evaluada sobre un modelo de minería de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Predict(Mining_Model_Name,String_Expression)   
```  
  
## <a name="arguments"></a>Argumentos  
 *Mining_Model_Name*  
 Expresión de cadena válida que representa el nombre de un modelo de minería de datos.  
  
 *String_Expression*  
 Expresión de cadena válida que se evalúa como una expresión DMX válida para el modelo de minería de datos especificado.  
  
## <a name="remarks"></a>Comentarios  
 El **Predict** función evalúa la expresión de cadena especificada en el contexto del modelo de minería de datos especificado.  
  
 La sintaxis y las funciones de minería de datos se documentan en la referencia de Expresiones de minería de datos (DMX).  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se predice nombre del clúster y la distancia desde él de un cliente determinado utilizando el modelo de minería de datos Customer Clusters:  
  
```  
WITH MEMBER MEASURES.CLNAME AS   
PREDICT("Customer Clusters", "Cluster()")  
MEMBER MEASURES.CLDISTANCE AS   
PREDICT("Customer Clusters", "ClusterDistance(Cluster())")  
SELECT {MEASURES.CLNAME, MEASURES.CLDISTANCE} ON 0   
FROM [Adventure Works]  
WHERE([Customer].[Customer Geography].[Customer].&[12012])  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de funciones MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
