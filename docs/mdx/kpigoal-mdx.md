---
title: KPIGoal (MDX) | Documentos de Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- KPIGoal function
ms.assetid: 0122c7d5-eefc-4819-b7a9-c80cd35505a8
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: fee69a33482cbc5f5dfe72e345d92bbe2e45d65d
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="kpigoal-mdx"></a>KPIGoal (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Devuelve el miembro que calcula el valor de la parte del objetivo del indicador clave de rendimiento (KPI) especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
KPIGoal(KPI_Name)  
```  
  
## <a name="arguments"></a>Argumentos  
 *Nombre_kpi*  
 Expresión de cadena válida que especifica el nombre de un KPI.  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente devuelve el valor del KPI, el objetivo del KPI, el estado del KPI y la tendencia del KPI de la medida Channel Revenue de los descendientes de tres miembros de la jerarquía de atributo Fiscal Year:  
  
```  
SELECT  
   { KPIValue("Channel Revenue"),   
     KPIGoal("Channel Revenue"),  
     KPIStatus("Channel Revenue"),   
     KPITrend("Channel Revenue")  
   } ON Columns,  
Descendants  
   ( { [Date].[Fiscal].[Fiscal Year].&[2002],  
       [Date].[Fiscal].[Fiscal Year].&[2003],  
       [Date].[Fiscal].[Fiscal Year].&[2004]   
     }, [Date].[Fiscal].[Fiscal Quarter]  
   ) ON Rows  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de funciones MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

