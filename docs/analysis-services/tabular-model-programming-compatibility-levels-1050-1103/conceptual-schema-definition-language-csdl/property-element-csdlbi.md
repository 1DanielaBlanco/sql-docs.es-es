---
title: Propiedad de elemento (CSDLBI) | Documentos de Microsoft
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
ms.assetid: f0770c5e-6420-4d0c-a5bf-b94eaf6877ca
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1fee5461b3b779227839c3f722c9c75626ed44fe
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2018
---
# <a name="property-element-csdlbi"></a>Property, elemento (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
El elemento Property en CSDLBI es un tipo complejo que proporciona características adicionales al elemento Property de CSDL para admitir modelos de datos de Business Intelligence.  
  
## <a name="elements-and-attributes"></a>Atributos y elementos  
 En la tabla siguiente se enumeran los elementos y atributos que definen el elemento Property de CSDLBI.  
  
|Nombre|Es obligatorio|Descripción|  
|----------|-----------------|-----------------|  
|Contenido|No|Cadena que contiene el LCID de la solicitud.|  
|DefaultAggregationFunction|Sí|Cadena que indica la función de agregación que se utilizará si se realizan cálculos en el atributo y no se ha especificado ninguna otra función.<br /><br /> Si no se especifica, se utiliza la agregación predeterminada para el modelo, que normalmente es SUM.|  
|GroupingBehavior|No|Valor que especifica cómo se agrupan los resultados de la consulta. El contenido del atributo se define mediante el tipo simple TGroupingBehavior (vea la tabla mostrada a continuación).|  
|OrderBy|No|Referencia a otra propiedad dentro del modelo que define la ordenación de los valores de esa propiedad.<br /><br /> Los valores de las dos propiedades DEBEN tener una asignación de uno a uno. En caso contrario, la ordenación quedará indefinida.<br /><br /> Si se omite este elemento, las propiedades se ordenan según sus valores.|  
|Stability|No|Atributo que especifica la estabilidad de los valores de propiedad entre operaciones de actualización.<br /><br /> Este atributo no lo establecen los usuarios, sino que lo emite el entorno en tiempo de diseño solo para los valores inestables. Siempre se aplica a las columnas que contienen un número de fila, y a las que contienen fórmulas que generan resultados indeterminados, como NOW() o RAND().<br /><br /> Los valores para este atributo se muestran en la tabla siguiente, que describe el tipo Stabilitysimple.|  
  
## <a name="groupingbehavior"></a>GroupingBehavior  
 En la tabla siguiente se enumeran los valores del tipo simple GroupingBehavior.  
  
|Value|Description|  
|-----------|-----------------|  
|GroupOnValue|Agrupa por el valor del atributo.|  
|GroupOnEntityKey|Agrupa por la clave de entidad.|  
  
 En el siguiente ejemplo se muestra el uso de estos dos valores. Supongamos que la consulta se diseñó para devolver deducciones de la nómina para un determinado usuario, especificado por su nombre. Si la base de datos contiene dos usuarios con el mismo nombre pero con identificadores de base de datos diferentes, los resultados de la consulta dependerán del valor de atributo que se aplique a la columna:  
  
-   **GroupOnValue**: consulta resultados incluyen las deducciones de nómina de ambos usuarios, sumadas conjuntamente.  
  
-   **GroupOnEntityKey**: consulta resultados incluyen las deducciones de nómina para cada usuario, pero enumeradas individualmente.  
  
## <a name="stability"></a>Stability  
 En la tabla siguiente se enumera los valores de la **estabilidad** tipo simple.  
  
|Value|Description|  
|-----------|-----------------|  
|Stable|La propiedad permanece constante entre operaciones de actualización.|  
|RowNumber|La propiedad contiene un número de fila.|  
|Volatile|Es posible que la propiedad no permanezca constante entre operaciones de actualización.|  
  
## <a name="example"></a>Ejemplo  
 **Tabular**  
  
 En el XML siguiente se muestra la representación, en la versión 1.1 de CSDLBI, de algunas propiedades en el ejemplo de modelo tabular AdventureWorks.  
  
```  
  
<EntityType   
   Name="DimEmployee">  
   <Key>  
      <PropertyRef   
      Name="RowNumber" />  
   </Key>  
  
   <Property   
      Name="RowNumber"   
      Type="Int64"   
      Nullable="false">  
   <bi:Property   
      Hidden="true"   
      Contents="RowNumber"   
      Stability="RowNumber" />  
   </Property>  
  
   <Property   
      Name="EmployeeKey"   
      Type="Int64">  
   <bi:Property />  
   </Property>  
….  
</bi:EntityType>  
</EntityType>  
  
```  
  
## <a name="example"></a>Ejemplo  
 **Multidimensionales**  
  
 En el ejemplo siguiente, en la versión 1.1 de CSDLBI, se muestran algunas propiedades de las columnas del modelo de datos que representan el cubo de operaciones de Contoso. Observe que no es necesario utilizar anotaciones BI en la mayoría de las columnas, solo en aquellas que requieren un tratamiento especial en el nivel de presentación.  
  
```  
  
<EntityType   
   Name="Bike">  
  
   <Key>  
      <PropertyRef Name="RowNumber" />  
   </Key>  
  
   <Property   
      Name="RowNumber"   
      Type="Int64"   
      Nullable="false">  
   <bi:Property   
      Hidden="true"   
      Contents="RowNumber"   
      Stability="RowNumber"   
   />  
   </Property>  
  
   <Property   
      Name="ProductAlternateKey"   
      Type="String"   
      MaxLength="Max"   
      Unicode="true"   
      FixedLength="false">  
   <bi:Property />  
   </Property>  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia técnica de anotaciones de BI para CSDL](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  
