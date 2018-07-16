---
title: Tipos de datos y XML (SQLXML 4.0) del comportamiento de carga de forma masiva | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], data types
- data types [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], data types
ms.assetid: d1ac1939-1f6c-4398-b7a7-a79ca608a4f1
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ce59362d28c4d65e32834fd965cf710f49edb501
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37274681"
---
# <a name="data-types-and-xml-bulk-load-behavior-sqlxml-40"></a>Tipos de datos y comportamiento de la carga masiva XML (SQLXML 4.0)
  Generalmente se omiten los tipos de datos que se especifican en el esquema de asignación (XSD o tipo XDR y `sql:datatype`), excepto en los casos siguientes:  
  
 En XSD:  
  
-   Si el tipo es `dateTime` o `time`, debe especificar `sql:datatype` porque la carga masiva XML realiza la conversión de datos antes de enviarlos a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Cuando se carga masiva en una columna de `uniqueidentifier` escriba [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] y el valor XSD es un GUID que incluye llaves ({y}), se debe especificar **SQL: DataType = "uniqueidentifier"** para quitar las llaves antes de que el valor es Insertar en la columna. Si no se especifica `sql:datatype`, el valor se envía con las llaves y se produce un error en la inserción.  
  
 Para obtener más información acerca de `sql:datatype`, consulte [conversiones de tipos de datos y la anotación SQL: DataType &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 En XDR:  
  
-   Si `dt:type` es `datetime`, `time`, `dateTime.tz` o `time.tz`, debe especificar los tipos de datos `dt:type` y `sql:datatype` porque la carga masiva XML realiza la conversión de datos antes de enviar los datos a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Si los datos XML están de tipo `uuid`, `sql:datatype` debe especificarse; **dt: Type = "uuid"** también es necesario, a menos que los datos son datos de cadena. Si no especifica `dt:uuid`, la carga masiva XML acepta cadenas con llaves (y las quita si es necesario).  
  
-   Si los datos XML son `bin.base64` o `bin.hex`, debe especificar el tipo de datos XML con `dt:type`. A continuación, la carga masiva XML carga los datos en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] como una representación hexadecimal de los datos.  
  
  
