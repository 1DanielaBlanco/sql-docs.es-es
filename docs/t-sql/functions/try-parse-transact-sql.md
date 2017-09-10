---
title: TRY_PARSE (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TRY_PARSE_TSQL
- TRY_PARSE
dev_langs:
- TSQL
helpviewer_keywords:
- TRY_PARSE function
ms.assetid: 292bac1d-edd8-468c-8ff1-8c7de625bc55
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 735d1e38b81a08da50cba340b0e5663d6e6d5755
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="tryparse-transact-sql"></a>TRY_PARSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Devuelve el resultado de una expresión, traducido al tipo de datos solicitado, o NULL si se produce un error en la conversión en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Use TRY_PARSE solo para convertir de tipos de cadena a tipos de fecha y hora y de número.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
TRY_PARSE ( string_value AS data_type [ USING culture ] )  
```  
  
## <a name="arguments"></a>Argumentos  
 *valor_cadena*  
 **nvarchar (4000)** valor que representa el valor con formato para analizar en el tipo de datos especificado.  
  
 *valor_cadena* debe ser una representación válida del tipo de datos solicitado o TRY_PARSE devuelve null.  
  
 *data_type*  
 Literal que representa el tipo de datos solicitado para el resultado.  
  
 *referencia cultural*  
 Cadena opcional que identifica la referencia cultural en la que *valor_cadena* tiene el formato.  
  
 Si el *referencia cultural* no se proporciona un argumento, se utiliza el idioma de la sesión actual. Este idioma se establece de forma implícita o explícitamente mediante la instrucción SET LANGUAGE. *referencia cultural* acepta cualquier referencia cultural compatible con .NET Framework; no se limita a los idiomas admitidos explícitamente por [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si el *referencia cultural* argumento no es válido, PARSE produce un error.  
  
## <a name="return-types"></a>Tipos devueltos  
 Devuelve el resultado de la expresión, traducido al tipo de datos solicitado, o NULL si se produce un error en la conversión.  
  
## <a name="remarks"></a>Comentarios  
 Use TRY_PARSE solo para convertir de tipos de cadena a tipos de fecha y hora y de número. Para las conversiones de tipos generales, siga usando CAST o CONVERT. Tenga en cuenta que hay cierta sobrecarga de rendimiento al analizar el valor de cadena.  
  
 TRY_PARSE se basa en la presencia de Common Language Runtime (CLR) de .NET Framework.  
  
 Esta función no se enviará de forma remota puesto que depende de la presencia del CLR. El envío remoto de una función que necesita el CLR produciría un error en el servidor remoto.  
  
 **Para obtener más información acerca del parámetro data_type**  
  
 Los valores para la *data_type* parámetro están restringidos a los tipos mostrados en la siguiente tabla, junto con estilos. La información de estilo se proporciona como ayuda para determinar los tipos de modelos permitidos. Para obtener más información sobre los estilos, consulte la documentación de .NET Framework para la **System.Globalization.NumberStyles** y **DateTimeStyles** enumeraciones.  
  
|Categoría|Tipo|Tipo de .NET|Estilos usados|  
|--------------|----------|---------------|-----------------|  
|Numérico|bigint|Int64|NumberStyles.Number|  
|Numérico|int|Int32|NumberStyles.Number|  
|Numérico|smallint|Int16|NumberStyles.Number|  
|Numérico|tinyint|Byte|NumberStyles.Number|  
|Numérico|decimal|Decimal|NumberStyles.Number|  
|Numérico|numeric|Decimal|NumberStyles.Number|  
|Numérico|float|Doble|NumberStyles.Float|  
|Numérico|real|Único|NumberStyles.Float|  
|Numérico|smallmoney|Decimal|NumberStyles.Currency|  
|Numérico|money|Decimal|NumberStyles.Currency|  
|Fecha y hora|date|DateTime|DateTimeStyles.AllowWhiteSpaces & #124; DateTimeStyles.AssumeUniversal|  
|Fecha y hora|time|Timespan|DateTimeStyles.AllowWhiteSpaces & #124; DateTimeStyles.AssumeUniversal|  
|Fecha y hora|datetime|DateTime|DateTimeStyles.AllowWhiteSpaces & #124; DateTimeStyles.AssumeUniversal|  
|Fecha y hora|smalldatetime|DateTime|DateTimeStyles.AllowWhiteSpaces & #124; DateTimeStyles.AssumeUniversal|  
|Fecha y hora|datetime2|DateTime|DateTimeStyles.AllowWhiteSpaces & #124; DateTimeStyles.AssumeUniversal|  
|Fecha y hora|datetimeoffset|DateTimeOffset|DateTimeStyles.AllowWhiteSpaces & #124; DateTimeStyles.AssumeUniversal|  
  
 **Para obtener más información acerca del parámetro de referencia cultural**  
  
 En la tabla siguiente se muestran las asignaciones de los idiomas de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a las referencias culturales de .NET Framework.  
  
|Nombre completo|Alias|LCID|Referencia cultural específica|  
|---------------|-----------|----------|----------------------|  
|us_english|Inglés|3082|es-ES|  
|Deutsch|Alemán|1031|de-DE|  
|Français|Francés|1036|fr-FR|  
|日本語|Japonés|1041|ja-JP|  
|Dansk|Danés|1030|da-DK|  
|Español|Español|3082|es-ES|  
|En italiano|Italiano|1040|it-IT|  
|Nederlands|Neerlandés|1043|nl-NL|  
|Norsk|Noruego|2068|nn-NO|  
|Português|Portugués|2070|pt-PT|  
|Suomi|Finlandés|1035|fi|  
|Svenska|Sueco|1053|sv-SE|  
|Čeština|Checo|1029|Cs-CZ|  
|magyar|Húngaro|1038|Hu-HU|  
|polski|Polaco|1045|Pl-PL|  
|română|Rumano|1048|Ro-RO|  
|hrvatski|Croata|1050|hr-HR|  
|slovenčina|Eslovaco|1051|Sk-SK|  
|slovenski|Esloveno|1060|Sl-SI|  
|ΕΛΛΗΝΙΚΆ|Griego|1032|El-GR|  
|БЪЛГАРСКИ|Búlgaro|1026|bg-BG|  
|РУССКИЙ|Ruso|1049|Ru-RU|  
|Türkçe|Turco|1055|Tr-TR|  
|British|British English|2057|en-GB|  
|eesti|Estonio|1061|Et-EE|  
|latviešu|Letón|1062|lv-LV|  
|lietuvių|Lituano|1063|lt-LT|  
|Português (Brasil)|Portugués de Brasil|1046|pt-BR|  
|繁體中文|Chino tradicional|1028|zh-TW|  
|한국어|Coreano|1042|Ko-KR|  
|简体中文|Chino simplificado|2052|zh-CN|  
|Árabe|Árabe|1025|ar-SA|  
|ไทย|Tailandés|1054|Th-TH|  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-simple-example-of-tryparse"></a>A. Ejemplo simple de TRY_PARSE  
  
```  
SELECT TRY_PARSE('Jabberwokkie' AS datetime2 USING 'en-US') AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
NULL  
  
(1 row(s) affected)  
```  
  
### <a name="b-detecting-nulls-with-tryparse"></a>B. Detectar valores NULL con TRY_PARSE  
  
```  
SELECT  
    CASE WHEN TRY_PARSE('Aragorn' AS decimal USING 'sr-Latn-CS') IS NULL  
        THEN 'True'  
        ELSE 'False'  
END  
AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
True  
  
(1 row(s) affected)  
```  
  
### <a name="c-using-iif-with-tryparse-and-implicit-culture-setting"></a>C. Usar IIF con TRY_PARSE y la configuración implícita de referencia cultural  
  
```  
SET LANGUAGE English;  
SELECT IIF(TRY_PARSE('01/01/2011' AS datetime2) IS NULL, 'True', 'False') AS Result;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
False  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vea también  
 [PARSE & #40; Transact-SQL & #41;](../../t-sql/functions/parse-transact-sql.md)   
 [Funciones de conversión & #40; Transact-SQL & #41;](../../t-sql/functions/conversion-functions-transact-sql.md)   
 [TRY_CONVERT & #40; Transact-SQL & #41;](../../t-sql/functions/try-convert-transact-sql.md)   
 [CAST y CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  
