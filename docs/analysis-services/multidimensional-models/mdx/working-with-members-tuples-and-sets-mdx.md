---
title: "Trabajar con miembros, tuplas y conjuntos (MDX) | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MDX [Analysis Services], tuplas"
  - "claves de miembro [MDX]"
  - "MDX [Analysis Services], conjuntos"
  - "miembros calculados [MDX]"
  - "miembros [MDX]"
  - "Expresiones multidimensionales [Analysis Services], miembros"
  - "conjuntos con nombre [MDX]"
  - "Expresiones multidimensionales [Analysis Services], tuplas"
  - "funciones de miembro [MDX]"
  - "conjuntos [MDX]"
  - "MDX [Analysis Services], miembros"
  - "nombres de miembro [MDX]"
  - "Expresiones multidimensionales [Analysis Services], conjuntos"
  - "funciones de tupla"
  - "tuplas"
  - "funciones de conjuntos [MDX]"
ms.assetid: b6ec2439-caef-46d3-9fd7-5f4526cee334
caps.latest.revision: 41
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 41
---
# Trabajar con miembros, tuplas y conjuntos (MDX)
  MDX proporciona varias funciones que devuelven uno o más miembros, tuplas o conjuntos; o que actúan sobre un miembro, tupla o conjunto.  
  
## Funciones de miembro  
 MDX proporciona varias funciones para recuperar miembros de otras entidades MDX, por ejemplo desde dimensiones, niveles, conjuntos o tuplas. Por ejemplo, [FirstChild](../../../mdx/firstchild-mdx.md) es una función que actúa sobre un miembro y devuelve un miembro.  
  
 Para obtener el primer miembro secundario de la dimensión Time, se debe indicar explícitamente el miembro, como en el siguiente ejemplo.  
  
```  
SELECT [Date].[Calendar Year].[CY 2001] on 0  
FROM [Adventure Works]  
  
```  
  
 También se puede utilizar la función **FirstChild** para devolver el mismo miembro, como se muestra en el siguiente ejemplo.  
  
```  
SELECT [Date].[Calendar Year].FirstChild on 0  
FROM [Adventure Works]  
  
```  
  
 Para obtener más información sobre las funciones de miembro de MDX, vea [Referencia de funciones MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md).  
  
## Funciones de tupla  
 MDX proporciona varias funciones que devuelven tuplas y que se pueden utilizar en cualquier ubicación en la que se acepte una tupla. Por ejemplo, la función [Item &#40;Tuple&#41; &#40;MDX&#41;](../../../mdx/item-tuple-mdx.md) puede usarse para extraer la primera tupla de un conjunto, lo que resulta muy útil cuando se sabe que un conjunto está compuesto por una sola tupla y se quiere proporcionar esa tupla a una función que requiere una.  
  
 El ejemplo siguiente devuelve la primera tupla desde el conjunto de tuplas en el eje de columna.  
  
```  
SELECT {  
   ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2003]  
   )  
, ([Measures].[Reseller Sales Amount]  
      ,[Date].[Calendar Year].[CY 2004]  
   )  
}.Item(0)  
ON COLUMNS   
FROM [Adventure Works]  
```  
  
 Para obtener más información sobre las funciones de tupla, vea [Referencia de funciones MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md).  
  
## Funciones de conjunto  
 MDX proporciona varias funciones que devuelven conjuntos. Escribir tuplas explícitamente y encerrarlas entre llaves no es la única manera de recuperar un conjunto. Para obtener más información sobre la función de miembros para devolver un conjunto, vea [Conceptos clave de MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md). Hay muchas más funciones de conjunto.  
  
 El operador dos puntos (:) permite utilizar el orden natural de los miembros para crear un conjunto. Por ejemplo, el conjunto que se muestra en el siguiente ejemplo incluye tuplas del primer al cuarto trimestre del año 2002.  
  
```  
SELECT   
   {[Calendar Quarter].[Q1 CY 2002]:[Calendar Quarter].[Q4 CY 2002]}   
ON 0  
FROM [Adventure Works]  
```  
  
 Si no utiliza el operador dos puntos para crear el conjunto, puede crear el mismo conjunto de miembros al especificar las tuplas en el siguiente ejemplo:  
  
```  
SELECT {  
   [Calendar Quarter].[Q1 CY 2002],   
   [Calendar Quarter].[Q2 CY 2002],   
   [Calendar Quarter].[Q3 CY 2002],   
   [Calendar Quarter].[Q4 CY 2002]  
   } ON 0  
FROM [Adventure Works]  
  
```  
  
 El operador dos puntos es una función inclusiva. Los miembros ubicados a ambos lados del operador dos puntos se incluyen en el conjunto resultante.  
  
 Para obtener más información sobre las funciones de conjuntos, vea [Referencia de funciones MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md).  
  
## Funciones de matriz  
 Una función de matriz actúa sobre un conjunto y devuelve una matriz. Para obtener más información sobre las funciones de matriz, vea [Referencia de funciones MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md).  
  
## Funciones de jerarquía  
 Una función de jerarquía devuelve una jerarquía al actuar sobre un miembro, un nivel, una jerarquía o una cadena. Para obtener más información sobre las funciones de jerarquía, vea [Referencia de funciones MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md).  
  
## Funciones de nivel  
 Una función de nivel devuelve un nivel al actuar sobre un miembro, un nivel o una cadena. Para obtener más información sobre las funciones de nivel, vea [Referencia de funciones MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md).  
  
## Funciones lógicas  
 Una función lógica actúa sobre una expresión MDX para devolver información acerca de las tuplas, miembros o conjuntos de la expresión. Por ejemplo, la función [IsEmpty &#40;MDX&#41;](../../../mdx/isempty-mdx.md) evalúa si una expresión ha devuelto un valor de celda vacía. Para obtener más información sobre las funciones lógicas, vea [Referencia de funciones MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md).  
  
## Funciones numéricas  
 Una función numérica actúa sobre una expresión MDX para devolver un valor escalar. Por ejemplo, la función [Aggregate &#40;MDX&#41;](../../../mdx/aggregate-mdx.md) devuelve un valor escalar que se calcula al agregar medidas sobre las tuplas de un conjunto especificado. Para obtener más información sobre las funciones numéricas, vea [Referencia de funciones MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md).  
  
## Funciones de cadena  
 Una función de cadena actúa sobre una expresión MDX para devolver una cadena. Por ejemplo, la función [UniqueName &#40;MDX&#41;](../../../mdx/uniquename-mdx.md) devuelve un valor de cadena que contiene el nombre único de una dimensión, jerarquía, nivel o miembro. Para obtener más información sobre las funciones de cadena, vea [Referencia de funciones MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md).  
  
## Vea también  
 [Conceptos clave de MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)   
 [Aspectos básicos de las consultas MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)   
 [Referencia de funciones MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)  
  
  