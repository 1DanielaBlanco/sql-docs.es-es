---
title: "query() (método del tipo de datos xml) | Microsoft Docs"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- query method
- query() method
ms.assetid: f48f6f7b-219f-463a-bf36-bc10f21afaeb
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 07ffca5e9c5a3d80ccd5e9a61ffb035ec718f805
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2018
---
# <a name="query-method-xml-data-type"></a>query() (método de tipo de datos xml)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Especifica una expresión XQuery en una instancia del tipo de datos **xml**. El resultado es de tipo **xml**. El método devuelve una instancia XML sin tipo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
query ('XQuery')  
```  
  
## <a name="arguments"></a>Argumentos  
 XQuery  
 Es una cadena, una expresión XQuery, que consulta nodos XML como, por ejemplo, elementos y atributos, en una instancia XML.  
  
## <a name="examples"></a>Ejemplos  
 En esta sección se muestran ejemplos de cómo usar el método query() del tipo de datos **xml**.  
  
### <a name="a-using-the-query-method-against-an-xml-type-variable"></a>A. Usar el método query() con una variable de tipo xml  
 El ejemplo siguiente declara una variable **@myDoc** de tipo **xml** y le asigna una instancia XML. Luego se usa el método **query()** para especificar una expresión XQuery en el documento.  
  
 La consulta recupera el elemento secundario <`Features`> del elemento <`ProductDescription`>:  
  
```  
declare @myDoc xml  
set @myDoc = '<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>  
</ProductDescription>  
</Root>'  
SELECT @myDoc.query('/Root/ProductDescription/Features')  
```  
  
 El resultado es el siguiente:  
  
```  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>        
```  
  
### <a name="b-using-the-query-method-against-an-xml-type-column"></a>B. Usar el método query() con una columna de tipo XML  
 En el ejemplo siguiente, el método **query()** se usa para especificar una expresión XQuery en la columna **CatalogDescription** de tipo **xml** de la base de datos **AdventureWorks**:  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
<Product ProductModelID="{ /PD:ProductDescription[1]/@ProductModelID }" />  
') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
declare namespace wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
     /PD:ProductDescription/PD:Features/wm:Warranty ') = 1  
```  
  
 Observe lo siguiente en la consulta anterior:  
  
-   La columna CatalogDescription es una columna **xml** con tipo. Esto quiere decir que tiene asociada una colección de esquemas. En el [Prólogo de XQuery](../../xquery/modules-and-prologs-xquery-prolog.md), la palabra clave **namespace** se usa para definir el prefijo que se va a usar posteriormente en el cuerpo de la consulta.  
  
-   El método **query()** crea XML, un elemento <`Product`> que tiene un atributo **ProductModelID**, en el que el valor de atributo **ProductModelID** se recupera a partir de la base de datos. Para obtener más información sobre la creación de XML, vea [Construcción de XML &#40;XQuery&#41;](../../xquery/xml-construction-xquery.md).  
  
-   [exist() (método del tipo de datos XML)](../../t-sql/xml/exist-method-xml-data-type.md) de la cláusula WHERE se usa para buscar únicamente filas que contengan el elemento <`Warranty`> en el XML. La palabra clave **namespace** se usa nuevamente para definir dos prefijos de espacio de nombres.  
  
 Éste es el resultado parcial:  
  
```  
<Product ProductModelID="19"/>   
<Product ProductModelID="23"/>   
...  
```  
  
 Observe que ambos métodos, query() y exist(), declaran el prefijo PD. En estos casos, puede utilizar WITH XMLNAMESPACES para definir los prefijos en primer lugar y utilizarlo en la consulta.  
  
```  
WITH XMLNAMESPACES 
(  
   'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD,  
   'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS WM
)  
SELECT CatalogDescription.query('<Product ProductModelID="{ /PD:ProductDescription[1]/@ProductModelID }" />')
       AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('/PD:ProductDescription/PD:Features/WM:Warranty ') = 1;

```  
  
## <a name="see-also"></a>Ver también  
 [Agregar espacios de nombres a consultas con WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Comparar XML con tipo y XML sin tipo](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Crear instancias de datos XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [métodos del tipo de datos xml](../../t-sql/xml/xml-data-type-methods.md)   
 [Lenguaje de manipulación de datos XML &#40;XML DML&#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
