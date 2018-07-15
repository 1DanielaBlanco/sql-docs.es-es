---
title: DisplayKey, elemento (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 7d881278-1e77-42e1-8cfc-f1bbd9ec2340
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: adcf9e8b2b87e0302158bbbf5652d8c32277170f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297155"
---
# <a name="displaykey-element-csdlbi"></a>DisplayKey, elemento (CSDLBI)
  El elemento DisplayKey contiene una lista de los elementos siguientes que constituyen en conjunto un identificador seguro. DisplayKey se encuentra solamente como elemento secundario del elemento EntityType. Puede hacer referencia a columnas o a extremos de rol.  
  
## <a name="elements-and-attributes"></a>Atributos y elementos  
 En la tabla siguiente se enumeran los atributos del elemento DisplayKey.  
  
|Nombre|Es obligatorio|Descripción|  
|----------|-----------------|-----------------|  
|IsDisplayKey|no|True o false.|  
  
## <a name="remarks"></a>Notas  
 Este elemento se utiliza en los informes. El elemento al que se aplica este atributo no tiene por qué ser la clave de tabla real, sino solo un elemento que se presentará como tal. Sin embargo, la columna que utilice para DisplayKey debe incluir valores únicos.  
  
## <a name="example"></a>Ejemplo  
 **Tabular**  
  
 En el ejemplo siguiente, en la versión 1.1 de CSDLBI, se muestra una columna del modelo de datos de ejemplo AdventureWorks que se ha designado como el elemento DisplayKey de la tabla.  
  
```  
<sample in progress>  
```  
  
## <a name="example"></a>Ejemplo  
 **Multidimensional**  
  
 En el ejemplo siguiente, en la versión 1.1 de CSDLBI, se muestra un extracto de la representación del cubo de operaciones de Contoso. En este modelo, se ha marcado la columna Color como la clave para mostrar de la tabla Bikes.  
  
```  
  
<EntityType   
    Name="Bike">  
.. .. ..  
<Property   
    Name="Color"   
    Type="String"   
    MaxLength="Max"   
    Unicode="true"   
    FixedLength="false">  
<bi:Property   
    ContextualNameRule="Context"   
    Alignment="Left" Units="counts"   
    SortDirection="Descending"   
    IsRightToLeft="true"   
    DefaultAggregateFunction="Max" />  
</Property>  
.. .. ..  
<bi:EntityType>  
   <bi:DisplayKey>  
      <bi:MemberRef Name="Color" />  
   </bi:DisplayKey>>  
.. .. ..  
</bi:EntityType>  
</EntityType>  
```  
  
## <a name="see-also"></a>Vea también  
 [Descripción del modelo de objetos tabulares](../representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [Conceptos de CSDLBI](../csdlbi-concepts.md)  
  
  
