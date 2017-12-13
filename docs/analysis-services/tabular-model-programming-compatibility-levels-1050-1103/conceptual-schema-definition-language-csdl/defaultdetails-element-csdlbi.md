---
title: DefaultDetails, elemento (CSDLBI) | Documentos de Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 05a08baa-23cc-4011-9c2e-f60a20bb87da
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b2755e08e3e509723e3c1b511c27f852be157ad3
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2017
---
# <a name="defaultdetails-element-csdlbi"></a>DefaultDetails, elemento (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]El elemento DefaultDetails representa una lista de referencias de propiedad que juntas definen el "campo predeterminado de conjunto" de columnas de la tabla. Cada propiedad solo puede hacer referencia a una medida o a una columna.  
  
## <a name="elements-and-attributes"></a>Atributos y elementos  
 En la tabla siguiente se enumeran los elementos y atributos que definen el elemento DefaultDetails.  
  
|Nombre|Es obligatorio|Descripción|  
|----------|-----------------|-----------------|  
|DefaultDetailsPosition|No|Entero positivo que indica la presencia y la posición en la colección.|  
  
## <a name="example"></a>Ejemplo  
 **Tabular**  
  
 En el ejemplo siguiente, en la versión 1.1 de CSDLBI, se muestra un extracto del modelo de datos de ejemplo AdventureWorks. Solo hay un conjunto de columnas predeterminado para la tabla Employees (Title). Sin embargo, se han definido tres columnas como el conjunto de campos predeterminado para la tabla Products.  
  
```  
  
<EntityType   
    Name="DimEmployee">  
....  
   <bi:DefaultDetails>  
      <bi:MemberRef Name="Title" />  
   </bi:DefaultDetails>  
.....  
<EntityType   
    Name="Products">  
.....  
   <bi:DefaultDetails>  
      <bi:MemberRef Name="Color" />  
      <bi:MemberRef Name="DealerPrice" />  
      <bi:MemberRef Name="Status" />  
   </bi:DefaultDetails>  
  
```  
  
## <a name="example"></a>Ejemplo  
 **Multidimensional**  
  
 En el ejemplo siguiente, en la versión 1.1 de CSDLBI, se muestra un extracto de la definición de la tabla Bike en el cubo de operaciones de Contoso. Esta anotación indica que la columna Color se debe mostrar de forma predeterminada si no se especifica ninguna otra columna de visualización.  
  
```  
  
<EntityType Name="Bike">  
   <Key>  
   <PropertyRef Name="RowNumber" />  
   </Key>  
....  
<bi:EntityType>  
   <bi:DisplayKey>  
      <bi:MemberRef Name="Color" />  
   </bi:DisplayKey>  
   <bi:DefaultDetails>  
      <bi:MemberRef Name="Color" />  
   </bi:DefaultDetails>  
   <bi:SortMembers>  
      <bi:MemberRef Name="Color" />  
   </bi:SortMembers>  
....  
</bi:EntityType>  
</EntityType>  
```  
  
## <a name="see-also"></a>Vea también  
 [Descripción del modelo de objetos tabulares en compatibilidad 1050 1103 a través de niveles](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Conceptos de CSDLBI](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdlbi-concepts.md)  
  
  
