---
title: IsTrainingCase (DMX) | Documentos de Microsoft
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
- IsTrainingCase
dev_langs:
- DMX
helpviewer_keywords:
- IsTrainingCase function
ms.assetid: 63eab315-e743-470d-9c4c-edfc3f4058a3
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ed062df083d4c11c635f9241eac38b4ec4406a32
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="istrainingcase-dmx"></a>IsTrainingCase (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Indica si un caso se utiliza como caso de entrenamiento para el modelo o estructura de minería de datos especificados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
IsTrainingCase()  
```  
  
## <a name="result-type"></a>Tipo de resultado  
 Devuelve **true** si el caso forma parte del conjunto de datos de entrenamiento; en caso contrario, **false**.  
  
## <a name="remarks"></a>Comentarios  
 Si utiliza el Asistente para minería de datos con el fin de crear una estructura de minería de datos y el modelo de minería de datos relacionado, de forma predeterminada, el 30 por ciento de los casos se reservan para utilizarse como conjunto de datos de prueba. Los casos restantes en el origen de datos que se especifica se utilizan para entrenar el modelo. Sin embargo, si se utiliza Extensiones de minería de Datos (DMX) para crear el modelo de minería de datos, de forma predeterminada, todos los datos se utilizan para entrenar el modelo y no se crea ningún conjunto de pruebas. Para habilitar la creación de un conjunto de datos de prueba, se deben establecer los parámetros de la cláusula WITH HOLDOUT.  
  
 Se puede determinar si los datos de una estructura de minería de datos determinada se han dividido en conjuntos de entrenamiento y de prueba observando el valor de las propiedades <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxCases%2A> y <xref:Microsoft.AnalysisServices.MiningStructure.HoldoutMaxPercent%2A>.  
  
> [!NOTE]  
>  Obtención de detalles debe habilitarse en el modelo si desea utilizar las funciones IsTrainingCase o IsTestCase para devolver detalles sobre los casos del modelo. Para obtener más información, vea [Habilitar la obtención de detalles para un modelo de minería](../analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md).  
  
 Para devolver casos que forman parte del conjunto de datos de prueba, use la función [IsTestCase &#40; DMX &#41;](../dmx/istestcase-dmx.md).  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se usa el modelo de minería de datos agrupación en clústeres en el escenario de distribución de correo directo en el [Tutorial básico de minería de datos](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). La consulta solo devuelve los casos que se utilizaron para entrenar el modelo de minería de datos. Además, los casos de entrenamiento se restringen a los clientes menores de 40 años.  
  
```  
SELECT *  
FROM [TM Clustering].CASES  
WHERE IsTrainingCase()  
AND [Age] <40  
```  
  
 Para obtener ejemplos de cómo consultar los casos que se usan en la minería de datos, vea [SELECT FROM &#60; modelo &#62;. CASOS &#40; DMX &#41; ](../dmx/select-from-model-cases-dmx.md) y [SELECT FROM &#60; estructura &#62;. CASOS](../dmx/select-from-structure-cases.md).  
  
## <a name="see-also"></a>Vea también  
 [Conjuntos de datos de aprendizaje y prueba](../analysis-services/data-mining/training-and-testing-data-sets.md)   
 [Funciones &#40; DMX &#41;](../dmx/functions-dmx.md)   
 [Consultas de minería de datos](../analysis-services/data-mining/data-mining-queries.md)  
  
  

