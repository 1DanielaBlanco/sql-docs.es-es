---
title: Método Execute (XMLA) | Documentos de Microsoft
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
api_name:
- Execute Method
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- EXECUTE
- urn:schemas-microsoft-com:xml-analysis#
- http://schemas.microsoft.com/analysisservices/2003/engine#
- microsoft.xml.analysis.execute
- urn:schemas-microsoft-com:xml-analysis#Execute
helpviewer_keywords:
- Execute method
ms.assetid: 0fff5221-7164-4bbc-ab58-49cf04c52664
caps.latest.revision: 34
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 5c32261e06788f366a6c5ce5af24c508b87a6882
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36105905"
---
# <a name="execute-method-xmla"></a>Método Execute (XMLA)
  Envía el XML para los comandos de Analysis (XMLA) a una instancia de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Están incluidas las solicitudes que conllevan transferencia de datos, como recuperar o actualizar los datos del servidor.  
  
 **Espacio de nombres** urn:schemas-microsoft-com:xml-analysis  
  
 **Acción SOAP** "urn: schemas-microsoft-com-analysis: ejecutar"  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
<Execute>  
   <Command>...</Command>  
   <Properties>...</Properties>  
   <Parameters>...</Parameters>  
</Execute>  
```  
  
## <a name="element-characteristics"></a>Características del elemento  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|None|  
|Valor predeterminado|None|  
|Cardinalidad|0-1: elemento opcional que aparece una y solo una.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elemento primario|None|  
|Elementos secundarios|[Comando](xml-elements-properties/command-element-xmla.md), [parámetros](xml-elements-properties/parameters-element-xmla.md), [propiedades](xml-elements-properties/properties-element-xmla.md)|  
  
## <a name="remarks"></a>Notas  
 El `Execute` método ejecuta comandos XMLA proporcionados en el `Command` elemento y devuelve cualquier dato resultante mediante XMLA [conjunto de filas](xml-data-types/rowset-data-type-xmla.md) tipo de datos (para conjuntos de resultados tabulares) o el XMLA [MDDataSet](xml-data-types/mddataset-data-type-xmla.md) tipo de datos (para conjuntos de resultados multidimensionales.)  
  
## <a name="example"></a>Ejemplo  
 El código siguiente es un ejemplo de una llamada al método  `Execute` que contiene una instrucción SELECT de Expresiones multidimensionales (MDX).  
  
```  
<Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <Command>  
      <Statement>  
         SELECT [Measures].MEMBERS ON COLUMNS FROM [Adventure Works]  
      </Statement>  
   </Command>  
   <Properties>  
      <PropertyList>  
         <DataSourceInfo>Provider=MSOLAP;Data Source=local;</DataSourceInfo>  
         <Catalog>Adventure Works DW Multidimensional 2012</Catalog>  
         <Format>Multidimensional</Format>  
         <AxisFormat>ClusterFormat</AxisFormat>  
      </PropertyList>  
   </Properties>  
</Execute>  
```  
  
## <a name="see-also"></a>Vea también  
 [Tipos de datos XML &#40;XMLA&#41;](xml-data-types/xml-data-types-xmla.md)   
 [Método Discover &#40;XMLA&#41;](xml-elements-methods-discover.md)   
 [Métodos &#40;XMLA&#41;](xml-elements-methods.md)   
 [Elementos XML &#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)   
 [Conjuntos de filas de esquema de Analysis Services](../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  