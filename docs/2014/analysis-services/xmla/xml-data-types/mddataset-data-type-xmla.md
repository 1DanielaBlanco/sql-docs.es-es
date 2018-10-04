---
title: Tipo de datos MDDataSet Data (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MDDataSet Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#MDDataSet
- MDDataSet
- urn:schemas-microsoft-com:xml-analysis#MDDataSet
helpviewer_keywords:
- MDDataSet data type
ms.assetid: 1a7e0092-f9f0-4ae5-ba27-ad1d8ebe8cb9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6d9208c800800032a2e79d58239132c5152b51b5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48124205"
---
# <a name="mddataset-data-type-xmla"></a>Tipo de datos MDDataSet Data (XMLA)
  Define un tipo de datos derivado que representa los datos multidimensionales devueltos por la [Execute](../xml-elements-methods-execute.md) método.  
  
 **Namespace** urn: schemas-microsoft-com-analysis: mddataset  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:rowset">  
   <!-- The following elements extend Resultset -->  
   <!-- Optional schema elements -->  
   <OlapInfo>...</OlapInfo>  
   <Axes>...</Axes>  
   <CellData>...</CellData>  
</root>  
```  
  
## <a name="data-type-characteristics"></a>Características del tipo de datos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipos de datos base|[Conjunto de resultados](resultset-data-type-xmla.md)|  
|Tipos de datos derivados|None|  
  
## <a name="data-type-relationships"></a>Relaciones entre tipos de datos  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|None|  
|Elementos secundarios|[Ejes](../xml-elements-properties/axes-element-xmla.md), [CellData](../xml-elements-properties/celldata-element-xmla.md), [OlapInfo](../xml-elements-properties/olapinfo-element-xmla.md)|  
|Elementos derivados|None|  
  
## <a name="remarks"></a>Comentarios  
 El tipo de datos `MDDataSet` proporciona el conjunto de filas (o conjunto de datos) orientado necesario para representar datos OLAP en XML. El contenido de este conjunto de filas puede variar según los valores de la `Content` y `Format` las propiedades incluidas en el [propiedades](../xml-elements-properties/properties-element-xmla.md) colección de los `Execute` método. Para obtener más información sobre la `Content` y `Format` propiedades, consulte [propiedades XMLA compatibles &#40;XMLA&#41;](../xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
 Para obtener información básica sobre OLE DB para las estructuras de conjunto de datos de OLAP, vea el tema acerca de la asignación del tipo de datos MDDataSet a OLE DB en la especificación XML for Analysis 1.1. Para obtener un ejemplo completo de lenguaje de definición de esquema XML (XSD) del tipo de datos `MDDataSet`, vea el "Apéndice D: ejemplo de MDDataSet" de la especificación XML XML for Analysis 1.1.  
  
## <a name="see-also"></a>Vea también  
 [Tipos de datos XML &#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  
