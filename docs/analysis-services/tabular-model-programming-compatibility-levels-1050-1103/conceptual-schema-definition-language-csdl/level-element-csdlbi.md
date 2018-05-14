---
title: Nivel de elemento (CSDLBI) | Documentos de Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 76fc2e9f2f6aa20c7c18a43e7b88df8d24e9d13b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="level-element-csdlbi"></a>Level, elemento (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  El elemento Level es un tipo complejo que define un solo nivel de una jerarquía  
  
## <a name="elements-and-attributes"></a>Atributos y elementos  
 En la tabla siguiente se enumeran los elementos y atributos que definen el elemento Level.  
  
|Nombre|Es obligatorio|Descripción|  
|----------|-----------------|-----------------|  
|Origen|Sí|Contenedor para la referencia de propiedad.|  
|PropertyRef|Sí|Referencia a una propiedad de instancia. Otros atributos del nivel, como títulos, nombre y nombre de referencia, se pueden obtener de la propiedad de instancia a la que se hace referencia. En tal caso, no necesita especificarlos en el elemento Level.|  
  
## <a name="remarks"></a>Comentarios  
 Para más información sobre las jerarquías en los modelos tabulares, vea [Hierarchy, elemento &#40;CSDLBI&#41;](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/hierarchy-element-csdlbi.md).  
  
## <a name="example"></a>Ejemplo  
 **Tabular**  
  
 En el ejemplo siguiente, en la versión 1.1 de CSDLBI, se muestra la definición de varios niveles en una jerarquía del ejemplo de modelo tabular AdventureWorks.  
  
```  
  
<bi:Hierarchy Name="Category">  
   <bi:Level Name="CategoryName">  
     <bi:Source>  
       <bi:PropertyRef Name="CategoryName" />  
     </bi:Source>  
   </bi:Level>  
   <bi:Level Name="ProductName">  
     <bi:Source>  
       <bi:PropertyRef Name="ProductName" />  
     </bi:Source>  
   </bi:Level>  
</bi:Hierarchy>  
```  
  
## <a name="example"></a>Ejemplo  
 **Multidimensionales**  
  
 En el ejemplo siguiente, en la versión 1.1 de CSDLBI, se muestra una jerarquía con varios niveles del cubo de operaciones de Contoso.  
  
```  
<bi:Hierarchy   
   Name="Product_Hierarchy"   
   Caption="Product Hierarchy"   
   ReferenceName="Product Hierarchy">  
     <bi:Documentation>  
        <bi:Summary>DESCRIPTION_ProductModelCateg_Hierarchies</bi:Summary>  
     </bi:Documentation>  
  
     <bi:Level Name="ProductLine">  
        <bi:Source>  
        <bi:PropertyRef Name="ProductLine" />  
        </bi:Source>  
     </bi:Level>  
  
     <bi:Level Name="ModelName">  
        <bi:Source>  
        <bi:PropertyRef Name="ModelName" />  
        </bi:Source>  
     </bi:Level>  
</bi:Hierarchy>  
```  
  
## <a name="see-also"></a>Vea también  
 [Descripción del modelo de objetos tabulares en compatibilidad 1050 1103 a través de niveles](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Descripción de las funciones para jerarquías de elementos primarios y secundarios en DAX](http://msdn.microsoft.com/en-us/b11f0cff-cee4-4ae7-a5b3-ebe288fc42d3)   
 [Configurar el & #40; Todas las & #41; Nivel de las jerarquías de atributo](../../../analysis-services/multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
