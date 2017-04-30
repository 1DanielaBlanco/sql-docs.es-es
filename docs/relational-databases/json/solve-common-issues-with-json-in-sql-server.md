---
title: Resolver problemas comunes con JSON en SQL Server | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 07/07/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JSON, FAQ
ms.assetid: feae120b-55cc-4601-a811-278ef1c551f9
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: abae3fc5a3d8edab6e4b465ce4cae038e45222d0
ms.lasthandoff: 04/11/2017

---
# <a name="solve-common-issues-with-json-in-sql-server"></a>Resolver problemas comunes con JSON en SQL Server
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 Encuentre respuestas en este artículo a algunas preguntas habituales sobre la compatibilidad integrada de JSON en SQL Server.  
 
## <a name="for-json-and-json-output"></a>Salida de FOR JSON y JSON

### <a name="for-json-path-or-for-json-auto"></a>¿FOR JSON PATH o FOR JSON AUTO?  
 **Pregunta.** Necesito crear un resultado de texto JSON a partir de una consulta SQL simple en una sola tabla. FOR JSON PATH y FOR JSON AUTO generan el mismo resultado. ¿Cuál de estas dos opciones debo usar?  
  
 **Respuesta.** Use FOR JSON PATH. Aunque no hay ninguna diferencia en el resultado JSON, el modo AUTO tiene alguna lógica adicional que comprueba si se deben anidar columnas. Considere la posibilidad de usar PATH como la opción predeterminada.  

### <a name="create-a-nested-json-structure"></a>Creación de una estructura anidada JSON  
 **Pregunta.** Necesito generar texto JSON con varias matrices del mismo nivel. FOR JSON PATH puede crear objetos anidados con rutas de acceso y FOR JSON AUTO crea el nivel de anidamiento adicional para cada tabla. Ninguna de estas dos opciones me permite generar el resultado deseado. ¿Cómo puedo crear un formato JSON personalizado que no admitan directamente las opciones existentes?  
  
 **Respuesta.** Puede crear cualquier estructura de datos agregando consultas FOR JSON como expresiones de columna que devuelvan texto JSON, o bien cree manualmente texto JSON mediante la función JSON_QUERY, tal y como se muestra en el ejemplo siguiente.  
  
```tsql  
SELECT col1, col2, col3,  
             (SELECT col11, col12, col13 FROM t11 WHERE t11.FK = t1.PK FOR JSON PATH) as t11,  
             (SELECT col21, col22, col23 FROM t21 WHERE t21.FK = t1.PK FOR JSON PATH) as t21,  
             (SELECT col31, col32, col33 FROM t31 WHERE t31.FK = t1.PK FOR JSON PATH) as t31,  
             JSON_QUERY('{"'+col4'":"'+col5+'"}' as t41  
FROM t1  
FOR JSON PATH  
```  
  
Cada resultado de una consulta FOR JSON o la función JSON_QUERY en las expresiones de columna se formatea como un subobjeto JSON anidado independiente y se incluye en el resultado principal.  

### <a name="prevent-double-escaped-json-in-for-json-output"></a>Prevención de texto JSON con caracteres de doble escape en el resultado FOR JSON  
 **Pregunta.** Tengo texto JSON almacenado en una columna de tabla. Quiero incluirlo en el resultado de FOR JSON. FOR JSON aplica caracteres de escape a todos los caracteres JSON, por lo que obtengo una cadena JSON en lugar de un objeto anidado, tal y como se muestra en el ejemplo siguiente.  
  
```tsql  
SELECT 'Text' as myText, '{"day":23}' as myJson  
FOR JSON PATH  
```  
  
 Esta consulta genera el siguiente resultado.  
  
```json  
[{"myText":"Text","myJson":"{\"day\":23}"}]  
```  
  
 ¿Cómo puedo evitar este comportamiento? Quiero que se devuelva `{"day":23}` como un objeto JSON y no como texto con caracteres de escape.  
  
 **Respuesta.** Los textos JSON almacenados en una columna de texto o un literal se tratan como cualquier texto. Va precedido y seguido de comillas dobles y caracteres de escape. Si desea que se devuelva un objeto JSON sin caracteres de escape, deberá pasar esta columna como argumento a la función JSON_QUERY, tal y como se muestra en el ejemplo siguiente.  
  
```tsql  
SELECT col1, col2, col3, JSON_QUERY(jsoncol1) AS jsoncol1  
FROM tab1  
FOR JSON PATH  
```  
  
 JSON_QUERY sin su segundo parámetro opcional devuelve solo el primer argumento como resultado. Puesto que JSON_QUERY devuelve texto JSON válido, FOR JSON reconoce que este resultado no tiene que ir con caracteres de escape.

### <a name="json-generated-with-the-withoutarraywrapper-clause-is-escaped-in-for-json-output"></a>Texto JSON generado con la cláusula WITHOUT_ARRAY_WRAPPER y con caracteres de escape en el resultado FOR JSON  
 **Pregunta.** Estoy tratando de dar formato a una expresión de columna mediante FOR JSON y la opción WITHOUT_ARRAY_WRAPPER.  
  
```tsql  
SELECT 'Text' as myText,  
       (SELECT 12 day, 8 mon FOR JSON PATH, WITHOUT_ARRAY_WRAPPER) as myJson  
FOR JSON PATH   
```  
  
 Parece que al texto que devuelve la consulta FOR JSON se le aplican caracteres de escape como texto sin formato. Esto solo sucede si se especifica WITHOUT_ARRAY_WRAPPER. ¿Por qué no se trata como un objeto JSON y se incluye sin caracteres de escape en el resultado?  
  
 **Respuesta.** Si se especifica la opción de WITHOUT_ARRAY_WRAPPER, el texto JSON generado no tiene por qué ser válido. Por lo tanto, la consulta JSON FOR exterior da por hecho que esto es texto sin formato y aplica caracteres de escape a la cadena. Si está seguro de que el resultado JSON es válido, inclúyalo con la función JSON_QUERY para promoverlo a JSON con formato correcto, tal y como se muestra en el ejemplo siguiente.  
  
```tsql  
SELECT 'Text' as myText,  
      JSON_QUERY((SELECT 12 day, 8 mon FOR JSON PATH, WITHOUT_ARRAY_WRAPPER)) as myJson  
FOR JSON PATH    
```  

## <a name="openjson-and-json-input"></a>Entrada de OPENJSON y JSON

### <a name="return-a-nested-json-sub-object-from-json-text-with-openjson"></a>Devolución de un subobjeto JSON anidado a partir de texto JSON con OPENJSON  
 **Pregunta.** No puedo abrir una matriz de objetos complejos JSON que contienen matrices, objetos y valores escalares empleando OPENJSON con un esquema explícito. Cuando hago referencia a una clave en la cláusula WITH, se devuelven solo los valores escalares. Los objetos y las matrices se devuelven como valores NULL. ¿Cómo puedo extraer objetos o matrices de objetos JSON?  
  
 **Respuesta.** Si quiere devolver un objeto o matriz como una columna, use la opción AS JSON en la definición de columna, tal y como se muestra en el ejemplo siguiente.  
  
```tsql  
SELECT scalar1, scalar2, obj1, obj2, arr1  
FROM OPENJSON(@json)  
             WITH ( scalar1 int,  
                          scalar2 datetime2,  
                          obj1 NVARCHAR(MAX) AS JSON,  
                          obj2 NVARCHAR(MAX) AS JSON,  
                          arr1 NVARCHAR(MAX) AS JSON)  
```  

### <a name="use-openjson-instead-of-jsonvalue-to-return-long-text-values"></a>Usar OPENJSON en lugar de JSON_VALUE para devolver valores de texto largo  
 **Pregunta.** Tengo una clave de descripción en JSON que contiene texto largo. `JSON_VALUE(@json, '$.description')` devuelve NULL en lugar de un valor.  
  
 **Respuesta.** JSON_VALUE se ha diseñado para devolver valores escalares de tamaño reducido. Generalmente, la función devuelve NULL en lugar de un error de desbordamiento. Si quiere que se devuelvan valores de mayor tamaño, utilice OPENJSON, que admite valores NVARCHAR(MAX), tal y como se muestra en el ejemplo siguiente.  
  
```tsql  
SELECT myText FROM OPENJSON(@json) WITH (myText NVARCHAR(MAX) '$.description')  
```  

### <a name="use-openjson-instead-of-jsonvalue-to-handle-duplicate-keys"></a>Usar OPENJSON en lugar de JSON_VALUE para gestionar las claves duplicadas  
 **Pregunta.** Tengo claves duplicadas en el texto JSON. JSON_VALUE devuelve solo la primera clave que se encuentra en la ruta de acceso. ¿Cómo puedo devolver todas las claves que tengan el mismo nombre?  
  
 **Respuesta.** Las funciones escalares integradas JSON devuelven solo la primera aparición del objeto de referencia. Si necesita más de una clave, utilice la función con valores de tabla OPENJSON, tal y como se muestra en el ejemplo siguiente.  
  
```tsql  
SELECT value FROM OPENJSON(@json, '$.info.settings')  
WHERE [key] = 'color'  
```  

### <a name="openjson-requires-compatibility-level-130"></a>OPENJSON requiere el nivel de compatibilidad 130  
 **Pregunta.** Estoy tratando de ejecutar OPENJSON en SQL Server 2016 y obtengo el siguiente error.  
  
 `Msg 208, Level 16, State 1 ‘Invalid object name OPENJSON’`  
  
 **Respuesta.** La función OPENJSON solo está disponible en el nivel de compatibilidad 130. Si el nivel de compatibilidad de base de datos es inferior a 130, OPENJSON estará oculto. Hay otras funciones JSON que sí están disponibles en todos los niveles de compatibilidad.  
 
## <a name="other-questions"></a>Otras preguntas

### <a name="reference-keys-that-contain-non-alphanumeric-characters-in-json-text"></a>Claves de referencia que contienen caracteres no alfanuméricos en texto JSON  
 **Pregunta.** Tengo caracteres no alfanuméricos en claves de mi texto JSON. ¿Cómo puedo hacer referencia a estas propiedades?  
  
 **Respuesta.** Tiene que incluirlas entre comillas en las rutas de acceso JSON. Por ejemplo, `JSON_VALUE(@json, '$."$info"."First Name".value')`.
 

