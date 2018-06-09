---
title: Tipo de datos MDDataSet Data (XMLA) | Documentos de Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 986fade6d9db3d6170d47181ac960d15febdf260
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34573927"
---
# <a name="mddataset-data-type-xmla"></a>Tipo de datos MDDataSet Data (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Define un tipo de datos derivado que representa datos multidimensionales devueltos por la [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) método.  
  
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
|Tipos de datos básicos|[Conjunto de resultados](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|  
|Tipos de datos derivados|Ninguno|  
  
## <a name="data-type-relationships"></a>Relaciones de tipo de datos  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|Ninguno|  
|Elementos secundarios|[Ejes](../../../analysis-services/xmla/xml-elements-properties/axes-element-xmla.md), [CellData](../../../analysis-services/xmla/xml-elements-properties/celldata-element-xmla.md), [OlapInfo](../../../analysis-services/xmla/xml-elements-properties/olapinfo-element-xmla.md)|  
|Elementos derivados|Ninguno|  
  
## <a name="remarks"></a>Comentarios  
 El **MDDataSet** tipo de datos proporciona el orientado conjunto de filas (o conjunto de datos) necesarios para representar los datos OLAP en XML. El contenido de este conjunto de filas puede variar según los valores de la **contenido** y **formato** las propiedades incluidas en el [propiedades](../../../analysis-services/xmla/xml-elements-properties/properties-element-xmla.md) colección de la  **Ejecutar** método. Para obtener más información sobre la **contenido** y **formato** propiedades, consulte [admite propiedades XMLA &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md).  
  
 Para obtener información básica sobre OLE DB para las estructuras de conjunto de datos de OLAP, vea el tema acerca de la asignación del tipo de datos MDDataSet a OLE DB en la especificación XML for Analysis 1.1. Para obtener un ejemplo de lenguaje (XSD) de definición de esquemas XML completo de la **MDDataSet** tipo de datos, consulte "Apéndice D: ejemplo de MDDataSet" de la especificación de XML for Analysis 1.1.  
  
## <a name="see-also"></a>Vea también
 [Tipos de datos XML &#40;XMLA&#41;](../../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)  
  
  
