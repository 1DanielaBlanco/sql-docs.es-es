---
title: Tipo de datos TableBinding (ASSL) | Documentos de Microsoft
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
apiname: TableBinding Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: TableBinding
helpviewer_keywords: TableBinding data type
ms.assetid: 3195dca4-82bf-46b7-a31f-5383586e3573
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 22c9b057ef8ae5623732fadf3daf41ed1734a6c0
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="tablebinding-data-type-assl"></a>Tipo de datos TableBinding (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Define un tipo de datos derivado que representa un enlace a una tabla.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<TableBinding>  
   <!-- The following elements extend TabularBinding -->  
   <DataSourceID>...</DataSourceID>  
   <DbTableName>...</DbTableName>  
   <DbSchemaName>...</DbSchemaName>  
</TableBinding>  
```  
  
## <a name="data-type-characteristics"></a>Características del tipo de datos  
  
|Característica|Description|  
|--------------------|-----------------|  
|Tipos de datos base|[TabularBinding](../../../analysis-services/scripting/data-type/tabularbinding-data-type-assl.md)|  
|Tipos de datos derivados|None|  
  
## <a name="data-type-relationships"></a>Relaciones entre tipos de datos  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|None|  
|Elementos secundarios|[DataSourceID](../../../analysis-services/scripting/properties/datasourceid-element-assl.md), [DbSchemaName](../../../analysis-services/scripting/properties/dbschemaname-element-assl.md), [DbTableName](../../../analysis-services/scripting/properties/dbtablename-element-assl.md)|  
|Elementos derivados|Vea [enlace](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Comentarios  
 Tenga en cuenta que la referencia a otras tablas en la expresión de filtro mediante subselect puede afectar al rendimiento de algunos orígenes de datos. Sin embargo, el diseñador puede controlar totalmente la expresión de SQL definiendo una consulta con nombre en la vista del origen de datos y, a continuación, haciendo referencia a ella.  
  
 El método de definición de enlaces para una partición es independiente del uso de tablas con particiones en la vista del origen de datos.  
  
 Considere, por ejemplo, un grupo de medidas cuya tabla predeterminada es "Sales", con las columnas Date, Product ID, Qty, Price y Amount (calculadas en la vista del origen de datos). A continuación, la partición "Sales97" podría usar la tabla "Sales97" con filtro " Year(Sales.Date) = 97."  
  
 La consulta efectiva es:  
  
```  
SELECT Date, Product ID, Qty, Price, Qty * Price AS Amount   
   FROM Sales97 As Sales  
   WHERE Year(Sales.Date) = 97  
```  
  
 La expresión calculada todavía es válida, aunque la expresión haya usado nombres de tabla calificados (por ejemplo, Sales.Qty). Lo mismo se aplica si en su lugar, la tabla se sustituye por alguna consulta "SELECT..." La cláusula FROM anterior se convertiría en "FROM SELECT... As Sales."  
  
 Para obtener más información sobre la **enlace** tipo, incluidas las tablas de objetos de Analysis Services Scripting Language (ASSL) del tipo **enlace** y la jerarquía de herencia de **deenlace** tipos, consulte [enlazar el tipo de datos &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/binding-data-type-assl.md).  
  
 Para obtener información general de enlaces de datos en ASSL, vea [orígenes de datos y enlaces &#40; SSAS Multidimensional &#41; ](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 El elemento correspondiente en el modelo de objetos de Analysis Management Objects (AMO) es <xref:Microsoft.AnalysisServices.TableBinding>.  
  
## <a name="see-also"></a>Vea también  
 [Tipo de enlace de datos &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)   
 [Orígenes de datos y enlaces &#40; SSAS Multidimensional &#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)   
 [Analysis Services Scripting Language tipos de datos XML &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
