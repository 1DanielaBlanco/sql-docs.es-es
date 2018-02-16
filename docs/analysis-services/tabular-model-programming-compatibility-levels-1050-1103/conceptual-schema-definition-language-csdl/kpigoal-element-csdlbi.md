---
title: Kpigoal, elemento (CSDLBI) | Documentos de Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: fd8afbe7-b57d-4b47-862d-eb7b2489c327
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4e15a18c55318373b41c8a4fabe7377aad5d9f00
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2018
---
# <a name="kpigoal-element-csdlbi"></a>KpiGoal, elemento (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
El elemento KpiGoal proporciona una referencia a la columna que se utiliza para definir el objetivo de un indicador clave de rendimiento ((KPI).  
  
 En CSDLBI, los KPI están basados en medidas, y el elemento Measure contiene la fórmula (si existe), mientras que otros metadatos asociados con el KPI se definen como parte del [KPI, elemento &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/kpi-element-csdlbi.md).  El elemento Kpigoal es un subtipo del elemento Kpi.  
  
## <a name="elements-and-attributes"></a>Atributos y elementos  
 En la tabla siguiente se enumeran los atributos que definen el elemento KpiGoal.  
  
|Nombre|Es obligatorio|Descripción|  
|----------|-----------------|-----------------|  
|PropertyRef|Sí|Referencia a la columna que contiene el valor objetivo del KPI.<br /><br /> El elemento Kpigoal debe contener exactamente un elemento PropertyRef.<br /><br /> Vea [PropertyRef, elemento &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/propertyref-element-csdlbi.md).|  
  
## <a name="example"></a>Ejemplo  
 **Tabular**  
  
 En el ejemplo siguiente, en la versión 1.1 de CSDLBI, se muestra un KPI del modelo de ejemplo AdventureWorks.  
  
```  
  
<Property Name="InternetCurrentSalesPerformance" Type="Double">  
  <bi:Measure>  
    <bi:Kpi StatusGraphic="Three Stars Colored">  
      <bi:KpiGoal>  
        <bi:PropertyRef Name="v_InternetCurrSalesPerf_Goal" />  
      </bi:KpiGoal>  
      <bi:KpiStatus>  
        <bi:PropertyRef Name="v_InternetCurrSalesPerf_Status" />  
      </bi:KpiStatus>  
    </bi:Kpi>  
  </bi:Measure>  
</Property>  
  
```  
  
## <a name="example"></a>Ejemplo  
 **Multidimensionales**  
  
 En el ejemplo siguiente, en la versión 1.1 de CSDLBI, se muestra un KPI del cubo de operaciones de Contoso.  
  
```  
<bi:Measure   
       Caption="Sum of SalesAmount"   
       ReferenceName="Sum of SalesAmount"   
       FormatString="\$#,0.00;(\$#,0.00);\$#,0.00">  
    <bi:Kpi   
       StatusGraphic="Three Circles Colored">  
      <bi:KpiGoal>  
         <bi:PropertyRef   
          Name="v_Sum_of_SalesAmount_Goal" />  
       </bi:KpiGoal>  
       <bi:KpiStatus>  
          <bi:PropertyRef   
          Name="v_Sum_of_SalesAmount_Status" />  
        </bi:KpiStatus>  
       </bi:Kpi>  
</bi:Measure>  
  
```  
  
## <a name="see-also"></a>Vea también  
 [KPI, elemento &#40; CSDLBI &#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/kpi-element-csdlbi.md)  
  
  
