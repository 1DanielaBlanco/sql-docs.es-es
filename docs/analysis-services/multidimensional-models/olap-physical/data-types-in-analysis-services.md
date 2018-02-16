---
title: Tipos de datos en Analysis Services | Documentos de Microsoft
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
applies_to:
- SQL Server 2016 Preview
ms.assetid: 910be4f4-3010-41cd-9fdc-f0a79a0ce823
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7fcf359a6f760ffffa4e1a0682e4c4b45f4fe272
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2018
---
# <a name="data-types-in-analysis-services"></a>Tipos de datos en Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Para todos los <xref:Microsoft.AnalysisServices.DataItem> objetos, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] admite el siguiente subconjunto de **System.Data.OleDb.OleDbType**. Para establecer o leer el tipo de datos, utilice [tipo de datos de elemento de datos &#40; ASSL &#41; ](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
## <a name="supported-data-types"></a>Tipos de datos admitidos  
  
|||  
|-|-|  
|Bigint|Entero de 64 bits con signo. El *BigInt* tipo de valor representa los enteros con valores comprendidos entre 9.223.372.036.854.775.808 a 9.223.372.036.854.775.807 positivo.|  
|Binario|Un flujo de datos binarios de **bytes** tipo. **Bytes** es un tipo de valor que representa los enteros sin signo con valores comprendidos entre 0 y 255.|  
|Boolean|Instancias de este tipo tienen el valor **true** o **false**.|  
|Moneda|A *moneda* valor comprendido entre -922.337.203.685.477,5808 y + 922.337.203.685.477,5807 con una precisión de una diezmilésima de unidad de moneda (cuatro lugares decimales).|  
|Date|Datos de fecha y hora, almacenados como valor double. La parte entera es el número de días transcurridos desde el 30 de diciembre de 1899 y la parte decimal es una fracción de un día o de una hora del día.|  
|Doble|Número de coma flotante de comprendido entre -1,79769313486232E +308 y 1,79769313486232E +308. Un valor Double almacena información numérica con una precisión de hasta 15 dígitos decimales.|  
|Integer|Entero de 32 bits que representa números enteros con signo con valores que comprendes desde el número 2.147.483.648 negativo hasta el número 2.147.483.647 positivo.|  
|Único|Número de coma flotante comprendido entre - 3,4028235E +38 y 3,4028235E +38. Un valor Single almacena información numérica con una precisión de hasta siete dígitos decimales.|  
|Smallint|Entero de 16 bits con signo. El *Smallint* tipo de valor representa los enteros con signo con valores comprendidos entre 32768 negativo al número 32767 positivo.|  
|Tinyint|Entero de 8 bits con signo. El tipo de valor Tinyint representa los enteros con valores que comprenden desde el número 128 negativo al número 127 positivo.|  
|UnsignedBigInt|Entero de 64 bits sin signo. El *UnsignedBigInt* tipo de valor representa los enteros sin signo con valores comprendidos entre 0 y 18.446.744.073.709.551.615.|  
|UnsignedInt|Entero de 32 bits sin signo. El *UnsignedInt* tipo de valor representa los enteros sin signo con valores comprendidos entre 0 y 4.294.967.295.|  
|UnsignedSmallInt|Entero de 16 bits sin signo. El *UnsignedSmallInt* tipo de valor representa los enteros sin signo con valores comprendidos entre 0 y 65535.|  
|UnsignedTinyInt|Entero de 8 bits sin signo. El *UnsignedTinyInt* tipo de valor representa los enteros sin signo con valores comprendidos entre 0 y 255.|  
|WChar|Flujo de caracteres Unicode terminado en NULL. A *WChar* es una colección secuencial de caracteres Unicode que se utiliza para representar texto.|  
  
## <a name="amo-validations-on-data-types"></a>Validaciones de AMO en tipos de datos  
 En la siguiente tabla se enumeran las validaciones adicionales que Objetos de administración de análisis (AMO) hace para determinados enlaces:  
  
|Object|Enlace|Tipos de datos admitidos|  
|------------|-------------|------------------------|  
|DimensionAttribute|KeyColumns|Todos excepto Binary|  
||NameColumn|Solo WChar|  
||SkippedLevelsColumn|Solo tipos integer: BigInt, Integer, SmallInt, TinyInt, UnsignedBigInt, UnsignedInt, UnsignedSmallInt, UnsignedTinyInt|  
||CustomRollupColumn|Solo WChar|  
||CustomRollupPropertiesColumn|Solo WChar|  
||UnaryOperatorColumn|Solo WChar|  
||ValueColumn|Todos|  
|AttributeTranslation|CaptionColumn|Solo WChar|  
|ScalarMiningStructureColumn|KeyColumns|Todos excepto Binary|  
||NameColumn|Solo WChar|  
|TableMiningStructureColumn|ForeignKeyColumns|Todos excepto Binary|  
|MeasureGroupAttribute|KeyColumns|Todos excepto Binary|  
|Medida de recuento distintiva|Origen|BigInt, Currency, Double, Integer, Single, SmallInt, TinyInt, UnsignedBigInt, UnsignedInt, UnsignedSmallInt, UnsignedTinyInt|  
  
  
