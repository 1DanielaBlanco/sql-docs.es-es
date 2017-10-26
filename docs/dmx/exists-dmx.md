---
title: Existe (DMX) | Documentos de Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Exists
dev_langs:
- DMX
helpviewer_keywords:
- Exists function
ms.assetid: 3b54dd93-f0a8-4f9a-96ae-a38bf977dda1
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: a42c5690b8c80ec752490605e3c3243ee78029de
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="exists-dmx"></a>Exists (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve **true** si la subconsulta especificada devuelve al menos una fila.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
EXISTS(<subquery>)  
```  
  
## <a name="arguments"></a>Argumentos  
 *subconsulta*  
 Una instrucción SELECT el formato SELECT * FROM \<nombre de columna > [donde \<lista de predicados >].  
  
## <a name="result-type"></a>Tipo de resultado  
 Devuelve **true** si el conjunto de resultados devuelto por la subconsulta contiene al menos una fila; en caso contrario, devuelve **false**.  
  
## <a name="remarks"></a>Comentarios  
 Puede utilizar la palabra clave NOT delante de EXISTS; por ejemplo, `WHERE NOT EXISTS (<subquery>)`.  
  
 La lista de columnas que se agrega al argumento de la subconsulta de EXISTS es irrelevante; la función solo comprueba la existencia de una fila que cumpla la condición.  
  
## <a name="examples"></a>Ejemplos  
 Puede utilizar EXISTS y NOT EXISTS para comprobar las condiciones en una tabla anidada. Esto es útil cuando se crea un filtro que controla los datos que se usan para entrenar o probar un modelo de minería de datos. Para obtener más información, vea [Filtros para modelos de minería &#40;Analysis Services - Minería de datos&#41;](../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).  
  
 El ejemplo siguiente se basa en el `[Association]` estructura de minería de datos y el modelo de minería de datos que creó en el [Tutorial básico de minería de datos](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). La consulta devuelve solo los casos en los que el cliente compró al menos un Patch kit.  
  
```  
SELECT * FROM [Association].CASES  
WHERE EXISTS  
(  
SELECT * FROM [v Assoc Seq Line Numbers]  
WHERE [[Model] = 'Patch kit'  
)  
```  
  
 Otra manera de ver los mismos datos que devuelven esta consulta es abrir el modelo en el Visor de asociación, haga clic en el conjunto de elementos **Patch kit = Existing**, seleccione la **obtener detalles** opción y, a continuación, seleccione **solo casos del modelo**.  
  
## <a name="see-also"></a>Vea también  
 [Funciones &#40; DMX &#41;](../dmx/functions-dmx.md)   
 [Sintaxis de filtro de modelo y ejemplos &#40; Analysis Services: minería de datos &#41;](../analysis-services/data-mining/model-filter-syntax-and-examples-analysis-services-data-mining.md)  
  
  

