---
title: xml (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xml_TSQL
- xml
dev_langs:
- TSQL
helpviewer_keywords:
- xml data type [SQL Server], about xml data type
ms.assetid: 9198f671-8e61-4ca4-9c3a-859f84020e62
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 6b9d3c8c512611ea9d8d0482acb7fd848c04629b
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="xml-transact-sql"></a>xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Es el tipo de datos que almacena datos de XML. Puede almacenar **xml** instancias en una columna o una variable de **xml** tipo.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
xml ( [ CONTENT | DOCUMENT ] xml_schema_collection )  
```  
  
## <a name="arguments"></a>Argumentos  
 CONTENT  
 Restringe la **xml** instancia sea de un fragmento XML con formato correcto. Los datos XML pueden contener cero o más elementos en el nivel superior. También se admiten nodos de texto en el nivel superior.  
  
 Éste es el comportamiento predeterminado.  
  
 DOCUMENT  
 Restringe la **xml** instancia sea de un documento XML bien formado. Los datos XML deben tener un elemento raíz (solo uno). No se admiten nodos de texto en el nivel superior.  
  
 *xml_schema_collection*  
 Es el nombre de una colección de esquemas XML. Para crear un tipo **xml** columna o variable, también puede especificar el nombre de colección de esquemas XML. Para obtener más información sobre con tipo y XML sin tipo, consulte [comparar XML con tipo y XML sin tipo](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
## <a name="remarks"></a>Comentarios  
 La representación almacenada de **xml** instancias de tipo de datos no pueden superar los 2 gigabytes (GB) de tamaño.  
  
 Las facetas CONTENT y DOCUMENT solo se aplican a XML con tipo. Para obtener más información, consulte [comparar XML con tipo y XML sin tipo](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
## <a name="examples"></a>Ejemplos  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @y xml (Sales.IndividualSurveySchemaCollection);  
SET @y =  (SELECT TOP 1 Demographics FROM Sales.Individual);  
SELECT @y;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [Conversiones de tipos de datos &#40; motor de base de datos &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)   
 [Tipos de datos &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Métodos de tipo de datos xml](../../t-sql/xml/xml-data-type-methods.md)   
 [Referencia del lenguaje XQuery &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md)  
  
  
