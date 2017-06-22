---
title: Escribir instrucciones Transact-SQL internacionales | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- writing international statements
- Transact-SQL international considerations
- international considerations [SQL Server], Transact-SQL
- Database Engine international considerations [SQL Server], Transact-SQL
- statements [SQL Server], international
- database international considerations [SQL Server], Transact-SQL
- dates [SQL Server], international considerations
ms.assetid: f0b10fee-27f7-45fe-aece-ccc3f63bdcdb
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8c73a4b7e8d9c3e470136942c830a0ba879ed420
ms.contentlocale: es-es
ms.lasthandoff: 06/22/2017

---
# <a name="write-international-transact-sql-statements"></a>Escribir instrucciones Transact-SQL internacionales
  Las bases de datos y las aplicaciones de bases de datos que utilizan instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)] obtendrán una mayor portabilidad de un idioma a otro, o admitirán varios idiomas, si se siguen estas directrices:  
  
-   Reemplace todos los usos de los tipos de datos **char**, **varchar**y **text** por **nchar**, **nvarchar**y **nvarchar(max)**. De esta forma, se evita problemas de conversión de páginas de códigos. Para más información, consulte [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
-   Cuando realice comparaciones y operaciones con los meses y días de la semana, utilice las partes numéricas de la fecha en lugar de cadenas de nombres. Las distintas configuraciones de idioma devuelven nombres diferentes para los meses y los días de la semana. Por ejemplo, DATENAME(MONTH,GETDATE()) devuelve May cuando el idioma está establecido en inglés de EE.UU. Mai cuando el idioma es alemán y mai cuando el idioma es francés. En su lugar, utilice una función como DATEPART que utiliza el número del mes en lugar del nombre. Utilice los nombres DATEPART cuando genere conjuntos de resultados que se van a mostrar al usuario ya que, generalmente, los nombres de fecha resultan más significativos que una representación numérica. No codifique, sin embargo, ninguna lógica que dependa de que los nombres mostrados estén en un idioma determinado.  
  
-   Cuando especifique fechas en las comparaciones o como entrada de las instrucciones INSERT o UPDATE, utilice constantes que se interpretan igual en todas las configuraciones de idioma:  
  
    -   Las aplicaciones ADO, OLE DB y ODBC deben utilizar la siguiente marca de tiempo, fecha y cláusulas de escape de hora ODBC:  
  
         **{ ts'**aaaa**-***mm***-***dd**hh***:***mm***:***ss*[**.***fff*] **'}** , como: **{ ts'**1998**-**09**-**24 10**:**02**:**20**' }**  
  
         **{ d'** *yyyy* **-** *mm* **-** *dd* **'}** such as: **{ d'**1998**-**09**-**24**'}**  
  
         **{ t'** *hh* **:** *mm* **:** *ss* **'}** such as: **{ t'**10:02:20**'}**  
  
    -   Las aplicaciones que utilizan otras API o desencadenadores, procedimientos almacenados y scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] deben utilizar las cadenas numéricas sin separar. Por ejemplo, *yyyymmdd* como en 19980924.  
  
    -   Las aplicaciones que usan otras API o scripts, procedimientos almacenados y desencadenadores [!INCLUDE[tsql](../../includes/tsql-md.md)] deben usar la instrucción CONVERT con un parámetro de estilo explícito para todas las conversiones entre los tipos de datos **time**, **date**, **smalldate**, **datetime**, **datetime2**y **datetimeoffset** y los tipos de datos de cadenas de caracteres. Por ejemplo, la siguiente instrucción se interpreta igual en todas las configuraciones de conexión de formato de fecha o de idioma:  
  
        ```  
        SELECT *  
        FROM AdventureWorks2012.Sales.SalesOrderHeader  
        WHERE OrderDate = CONVERT(DATETIME, '20060719', 101)  
        ```  
  
         Para obtener más información, vea [CAST y CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md).  
  
  
