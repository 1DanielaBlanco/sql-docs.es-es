---
title: "Crear consultas de obtención de detalles usando DMX | Documentos de Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42c896ee-e5ee-4017-b66e-31d1fe66d369
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dda090411aae5baf577c49e76176eab2835c1df9
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2018
---
# <a name="create-drillthrough-queries-using-dmx"></a>Crear consultas de obtención de detalles usando DMX
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Para todos los modelos que admitan la obtención de detalles, puede recuperar los datos de los casos y los datos de la estructura creando una consulta DMX en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o en cualquier otro cliente que soporte DMX.  
  
> [!WARNING]  
>  Para ver los datos, debe estar habilitada la obtención de detalles y es necesario tener los permisos necesarios.  
  
## <a name="specifying-drillthrough-options"></a>Especificar las opciones de la obtención de detalles  
 La sintaxis general para recuperar los casos de modelos y de estructuras es la siguiente:  
  
```  
SELECT <model column list>, StructureColumn('<structure column name') FROM <modelname>.CASES  
```  
  
 Para más información sobre el uso de consultas DMX para devolver datos de casos, vea [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](../../dmx/select-from-model-cases-dmx.md) y [SELECT FROM &#60;estructura&#62;.CASES](../../dmx/select-from-structure-cases.md).  
  
## <a name="examples"></a>Ejemplos  
 La siguiente consulta DMX devuelve los datos de los casos para una serie de productos concreta de un modelo de serie temporal. La consulta también devuelve la columna **Amount**, que no se usó en el modelo pero que está disponible en la estructura de minería de datos.  
  
```  
SELECT [DateSeries], [Model Region], Quantity, StructureColumn('Amount') AS [M200 Pacific Amount]  
FROM Forecasting.CASES  
WHERE [Model Region] = 'M200 Pacific'  
```  
  
 Observe que en este ejemplo, se ha usado un alias para cambiar el nombre de la columna de estructura. Si no asigna un alias a la columna de estructura, la columna se devuelve con el nombre 'Expression'. Este es el comportamiento predeterminado para todas las columnas sin nombre.  
  
## <a name="see-also"></a>Vea también  
 [Las consultas de obtención de detalles &#40; minería de datos &#41;](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)   
 [Obtención de detalles en estructuras de minería de datos](../../analysis-services/data-mining/drillthrough-on-mining-structures.md)  
  
  
