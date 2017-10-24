---
title: local-nombre-de-QName (XQuery) | Documentos de Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:local-name-from-QName function
- local-name-from-QName function
ms.assetid: fafed718-8c3c-403f-93ee-ec51fc157a6e
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 506a9923b8c74ecb022e6f3ba21305fb28ca49de
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="functions-related-to-qnames---local-name-from-qname"></a>Las funciones relacionadas con QNames - nombre local de QName
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve un xs: NCName que representa la parte local del QName especificado por *$arg*. El resultado es una secuencia vacía si *$arg* es una secuencia vacía.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
fn:local-name-from-QName($arg as xs:QName?) as xs:NCName?  
```  
  
## <a name="arguments"></a>Argumentos  
 *$arg*  
 Es el QName del que se debería extraer el nombre local.  
  
## <a name="examples"></a>Ejemplos  
 Este tema ofrecen ejemplos de XQuery con instancias XML almacenadas en varias **xml** escriba columnas en la [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] base de datos.  
  
 En el ejemplo siguiente se usa el **local-name-from-QName()** función para recuperar el nombre local y URI de espacio de nombres de elementos de un valor de tipo QName. En el ejemplo, se realizan las tareas siguientes:  
  
-   Crear una colección de esquemas XML.  
  
-   Crear una tabla con una columna de tipo xml. El tipo xml se escribe utilizando la colección de esquemas XML.  
  
-   Almacenar una instancia XML de ejemplo en la tabla. Mediante el **query()** método del tipo de datos xml, la expresión de consulta se ejecuta para recuperar la parte del nombre local del valor de tipo QName de la instancia.  
  
```  
DROP TABLE T  
go  
DROP XML SCHEMA COLLECTION SC  
go  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
targetNamespace="QNameXSD" >  
      <element name="root" type="QName" nillable="true"/>  
</schema>'  
go  
  
CREATE TABLE T (xmlCol XML(SC))  
go  
-- following OK  
insert into T values ('<root xmlns="QNameXSD" xmlns:a="http://someURI">a:someLocalName</root>')  
 go  
-- Retrieve the local name.   
SELECT xmlCol.query('declare default element namespace "QNameXSD"; local-name-from-QName(/root[1])')  
FROM T  
-- Result = someLocalName  
-- You can retrive namespace URI part from the QName using the namespace-uri-from-QName() function  
SELECT xmlCol.query('declare default element namespace "QNameXSD"; namespace-uri-from-QName(/root[1])')  
FROM T  
-- Result = http://someURI  
```  
  
## <a name="see-also"></a>Vea también  
 [Funciones relacionadas con QNames &#40; XQuery &#41;](http://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)  
  
  

