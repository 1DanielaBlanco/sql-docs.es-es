---
title: Cálculos | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f2f137312af7b4ef7d77334b3830cd337a849f42
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2018
ms.locfileid: "38983929"
---
# <a name="calculations"></a>Cálculos 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Después de importar datos en el modelo, puede agregar cálculos para agregar, filtrar, ampliar, combinar y proteger esos datos. Los modelos tabulares utilizan Expresiones de análisis de datos (DAX), un lenguaje de fórmulas para crear cálculos personalizados. En los modelos tabulares, los cálculos que crea mediante fórmulas DAX se utilizan en *Columnas calculadas*, *Medidas*y *Filtros de fila*.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Descripción de DAX en modelos tabulares](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md)|Describe el lenguaje de fórmulas Expresiones de análisis de datos (DAX) que se utiliza para crear cálculos para columnas calculadas, medidas y filtros de fila en modelos tabulares.|  
|[Compatibilidad de las fórmulas DAX en el modo DirectQuery](http://msdn.microsoft.com/981b6a68-434d-4db6-964e-d92f8eb3ee3e)|Se describen las diferencias, se enumeran las funciones que no se admiten en el modo DirectQuery y se enumeran las funciones que sí se admiten pero pueden devolver resultados distintos.|  
|[Referencia de expresiones (DAX) de análisis de datos](http://msdn.microsoft.com/70a82136-0926-4a91-bcb3-e18e82593b0d)|En esta sección se proporcionan descripciones detalladas de sintaxis, operadores, y funciones de DAX.|  
  
> [!NOTE]  
>  En esta sección no se proporcionan las tareas paso a paso para crear cálculos. Dado que los cálculos se especifican en columnas calculadas, medidas y filtros de fila (en roles), se proporcionan instrucciones sobre dónde crear fórmulas DAX en las tareas relacionadas con esas características. Para obtener más información, consulte [crear una columna calculada](../../analysis-services/tabular-models/ssas-calculated-columns-create-a-calculated-column.md), [crear y administrar medidas](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md), y [crear y administrar Roles](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md).  
  
> [!NOTE]  
>  Si bien DAX también se puede utilizar para consultar un modelo tabular, los temas de esta sección se centran concretamente en el uso de fórmulas DAX para crear cálculos.  
  
  
