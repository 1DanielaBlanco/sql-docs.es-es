---
title: KPITrend (MDX) | Documentos de Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- KPITrend function
ms.assetid: 0afd4513-af6e-4517-8e69-177bc7807d03
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 01476374e7fdb320a500a2e6afcdf28cbf27627b
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="kpitrend-mdx"></a>KPITrend (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve el valor normalizado que representa la parte de la tendencia del indicador clave de rendimiento (KPI) especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
KPITrend(KPI_Name)  
```  
  
## <a name="arguments"></a>Argumentos  
 *Nombre_kpi*  
 Expresión de cadena válida que especifica el nombre del KPI.  
  
## <a name="remarks"></a>Comentarios  
 El valor de tendencia suele ser un valor normalizado entre -1 y 1.  
  
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
  
  

