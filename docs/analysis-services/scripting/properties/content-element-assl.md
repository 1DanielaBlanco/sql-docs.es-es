---
title: Contenido de elemento (ASSL) | Documentos de Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e0efd6cc31b00c4029e88adab40b56aa88f50dc8
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="content-element-assl"></a>Elemento Content (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Describe el contenido de la columna en la [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<ScalarMiningStructureColumn>  
   ...  
   <Content>...</Content>  
   ...  
</ScalarMiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|String (enumeración)|  
|Valor predeterminado|Ninguno|  
|Cardinalidad|1-1: Elemento requerido que puede aparecer una y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elemento primario|[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|Elementos secundarios|Ninguno|  
  
## <a name="remarks"></a>Comentarios  
 Esta enumeración describe el tipo de contenido representado por una columna de estructura de minería de datos y se puede extender según sea necesario minando los proveedores del algoritmo. Para obtener más información sobre los tipos de contenido, vea [Tipos de contenido &#40;minería de datos&#41;](../../../analysis-services/data-mining/content-types-data-mining.md).  
  
 Todos los proveedores de algoritmo de minería de datos admiten normalmente los valores enumerados en la tabla siguiente.  
  
|Value|Description|  
|-----------|-----------------|  
|*Discretos*|La columna contiene valores discretos.|  
|*Continuo*|Los valores para la columna definen un conjunto continuo de datos numéricos.|  
|*Datos discretos*|Los valores de la columna representan grupos (o depósitos) de valores que se derivan de una columna continua.|  
|*ordenada*|Los valores de la columna definen un conjunto ordenado.|  
|*Cíclico*|Los valores de la columna definen un conjunto ordenado cíclico.|  
|*Probabilidad*|Los valores de la columna especifican una probabilidad para las columnas contenidas en el [ClassifiedColumns](../../../analysis-services/scripting/collections/classifiedcolumns-element-assl.md) elemento del elemento primario **ScalarMiningStructureColumn**.|  
|*Variance*|Los valores de la columna especifican una varianza para las columnas contenidas en el **ClassifiedColumns** elemento del elemento primario **ScalarMiningStructureColumn**.|  
|*StdDev*|Los valores de la columna especifican una desviación estándar para las columnas contenidas en el **ClassifiedColumns** elemento del elemento primario **ScalarMiningStructureColumn**.|  
|*ProbabilityVariance*|Los valores de la columna especifican una probabilidad para las columnas contenidas en el **ClassifiedColumns** elemento del elemento primario **ScalarMiningStructureColumn**.|  
|*ProbabilityStdDev*|Los valores de la columna especifican una desviación estándar para las columnas contenidas en el **ClassifiedColumns** elemento del elemento primario **ScalarMiningStructureColumn**.|  
|*Soporte técnico*|Los valores de la columna especifican información de soporte técnico para las columnas contenidas en el **ClassifiedColumns** elemento del elemento primario **ScalarMiningStructureColumn**.<br /><br /> Nota: Esta columna se proporciona como parte de la norma para proveedores de algoritmos de minería de datos de otros fabricantes. Microsoft proporciona algoritmos no hacen uso de esta columna.|  
|*Key*|La columna es una columna de clave.<br /><br /> Nota: Este tipo de contenido es aplicable únicamente a las columnas de clave, en el que el **IsKey** elemento está establecido en **True**.|  
  
 Además de estos valores no estándar, incluidos con los proveedores de algoritmos de minería de datos [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] admiten los valores en la tabla siguiente.  
  
|Value|Description|  
|-----------|-----------------|  
|*Secuencia de teclas*|La columna es una columna de clave y los valores de la columna representan una secuencia de eventos.<br /><br /> Nota: Este tipo de contenido es aplicable únicamente a las columnas de clave, en el que el **IsKey** elemento está establecido en **True**.|  
|*Clave temporal*|La columna es una columna de clave y los valores de la columna representan unidades de medida de tiempo.<br /><br /> Nota: Este tipo de contenido es aplicable únicamente a las columnas de clave, en el que el **IsKey** elemento está establecido en **True**.|  
|*Secuencia*|Los valores de la columna representan un flujo de eventos.|  
|*Time*|Los valores para la columna representan las unidades de medida de tiempo.|  
  
 La enumeración que corresponde a los valores permitidos para **contenido** en el objeto de Analysis Management Objects (AMO) es el modelo <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Vea también  
 [Elemento ClassifiedColumns &#40;ASSL&#41;](../../../analysis-services/scripting/collections/classifiedcolumns-element-assl.md)   
 [Propiedades & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
