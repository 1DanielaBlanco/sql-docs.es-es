---
title: Axes (XMLA) del elemento | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3a8dfff1c8a551157661bcb1de5700bf51a7f914
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38038023"
---
# <a name="axes-element-xmla"></a>Elemento Axes (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene una colección de [eje](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md) elementos que representan datos de eje contenidos por un [raíz](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) elemento que usa el [MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md) tipo de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">  
   ...  
   <Axes>  
      <Axis>...</Axis>  
   </Axes>  
   ...  
</root>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|Cualquiera|  
|Valor predeterminado|None|  
|Cardinalidad|1-1: Elemento necesario que se produce una vez y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones de elementos  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[raíz](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|Elementos secundarios|[Axis](../../../analysis-services/xmla/xml-elements-properties/axis-element-xmla.md)|  
  
## <a name="remarks"></a>Notas  
 En el **ejes** elemento, el **eje** elementos aparecen en el orden que aparecen en el conjunto de datos, empezando desde cero. El **AxisFormat** determina la configuración de la propiedad XMLA cómo **eje** se da formato a los elementos. Para obtener más información sobre la **AxisFormat** propiedad, vea [propiedades XMLA compatibles &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
 Un eje representa un conjunto de tuplas, en las que todas las tuplas del conjunto tienen la misma dimensionalidad. Un conjunto se puede representar de maneras diferentes con ventajas diferentes. Por ejemplo, el conjunto siguiente de cuatro tuplas se puede representar como una colección de tuplas bidimensionales o un producto cartesiano de dos conjuntos unidimensionales.  
  
|1999|1999|2000|2000|  
|----------|----------|----------|----------|  
|Real|Presupuesto|Real|Presupuesto|  
  
 Este conjunto de tuplas se puede representar como una colección de tuplas bidimensionales:  
  
```  
{ ( 1999, Actual ), ( 1999, Budget ), ( 2000, Actual ), ( 2000, Budget ) }  
```  
  
 Este conjunto también se puede representar como un producto cartesiano de dos conjuntos unidimensionales:  
  
```  
{ 1999, 2000 } x { Actual, Budget }  
```  
  
 Para las herramientas cliente es más fácil usar la primera representación, la colección de tuplas bidimensionales. La segunda representación, un producto cartesiano de conjuntos unidimensionales, utiliza menos espacio y conserva la naturaleza multidimensional del conjunto.  
  
 La tabla siguiente enumera las operaciones que se pueden usar para definir y caracterizar la estructura y los miembros de un eje.  
  
|Operación|Descripción|  
|---------------|-----------------|  
|Miembro|La unidad más pequeña de un eje que representa el miembro de una jerarquía de la dimensión.|  
|Miembros|Una colección de **miembro** objetos desde la misma jerarquía de la dimensión.|  
|Tuple|Una colección de miembros de diferentes jerarquías de la dimensión.|  
|Tuplas|Una colección de **tupla** objetos con la misma dimensionalidad.|  
|Union|Una unión de conjuntos.|  
|CrossJoin|Un producto cartesiano de conjuntos.|  
  
 Estas operaciones traducen las tuplas bidimensionales y el producto cartesiano de conjuntos unidimensionales como sigue.  
  
## <a name="two-dimensional-tuples"></a>Tuplas bidimensionales  
  
```  
Tuples (  
   Tuple( Member(1999), Member(Actual) ),  
   Tuple( Member(1999), Member(Budget) ),  
   Tuple( Member(2000), Member(Actual) ),  
   Tuple( Member(2000), Member(Budget) )  
```  
  
## <a name="cartesian-product-of-one-dimensional-sets"></a>Producto cartesiano de conjuntos unidimensionales  
  
```  
CrossProduct (  
   Members( Member(1999), Member(2000) ),  
   Members( Member(Actual), Member(Budget) )  
```  
  
 Un cliente puede utilizar el **AxisFormat** propiedad para solicitar una representación concreta.  
  
## <a name="see-also"></a>Vea también
 [Tipo de datos MDDataSet &#40;XMLA&#41;](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)   
 [Propiedades &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
