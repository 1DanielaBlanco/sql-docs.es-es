---
title: Elemento Create (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Create Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Create
- urn:schemas-microsoft-com:xml-analysis#Create
- microsoft.xml.analysis.create
helpviewer_keywords:
- Create command (XMLA)
ms.assetid: a623d362-a1ac-40e4-8816-65fac89cb391
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b64f6b222793fdd7c6b92e7462fc10976c0bc139
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48051295"
---
# <a name="create-element-xmla"></a>Elemento Create (XMLA)
  Contiene elementos de Analysis Services Scripting Language (ASSL) utilizados por el `Execute` método para crear objetos en un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instancia.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Command>  
   <Create Scope="enum" AllowOverwrite="boolean">  
      <ParentObject>...</ParentObject>  
      <ObjectDefinition>...</ObjectDefinition>  
   </Create>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|None|  
|Valor predeterminado|None|  
|Cardinalidad|0-n: elemento opcional que puede aparecer más de una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Elementos secundarios|[ObjectDefinition](../xml-elements-properties/objectdefinition-element-xmla.md), [ParentObject](../xml-elements-properties/object-element-xmla.md)|  
  
## <a name="attributes"></a>Atributos  
  
|Attribute|Descripción|  
|---------------|-----------------|  
|AllowOverwrite|Opcional `Boolean` atributo. Si está establecido en True, los objetos definidos en el elemento `ObjectDefinition` pueden sobrescribir objetos existentes en la instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Si este atributo se omite o se establece en False, la presencia de un objeto existente genera un error.|  
|Ámbito|Opcional `Enum` atributo. Define la duración de objetos definidos en el elemento `ObjectDefinition`. Si se omite este atributo, los objetos definidos en el elemento `ObjectDefinition` se almacenan en la instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Puede disponer de los siguientes valores:<br /><br /> -   *Sesión*<br />     Los objetos definidos en el elemento `ObjectDefinition` solamente existen mientras dura la sesión de XML  for Analysis (XMLA). **Nota:** cuando se usa el *sesión* establecimiento, el `ObjectDefinition` solo puede contener el elemento [dimensión](../../scripting/objects/dimension-element-assl.md), [cubo](../../scripting/objects/cube-element-assl.md), o [MiningModel ](../../scripting/objects/miningmodel-element-assl.md) Elementos ASSL.|  
  
## <a name="remarks"></a>Comentarios  
 Cada operación `Create` crea un objeto principal bajo un elemento primario proporcionado por el elemento `ParentObject`. Si se omite el objeto primario, se asume que es la instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] de destino. Esto genera un error si el elemento primario de un objeto principal no es la instancia de destino.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se crea una base de datos vacía denominada `Test Database` en una instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
```  
  
      <Create xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
   <ObjectDefinition>  
      <Database xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
         <Name>Test Database</Name>  
         <Description>A test database.</Description>  
      </Database>  
   </ObjectDefinition>  
</Create>  
```  
  
## <a name="see-also"></a>Vea también  
 [Comandos &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
