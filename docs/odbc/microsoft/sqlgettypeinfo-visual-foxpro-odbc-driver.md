---
title: SQLGetTypeInfo (controlador ODBC de Visual FoxPro) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5f25e20b-a4ef-42da-aeb6-00e0510fb1cc
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9bbf3983ccdeb2c320f4776d608b73e362f0a479
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgettypeinfo-visual-foxpro-odbc-driver"></a>SQLGetTypeInfo (controlador ODBC de Visual FoxPro)
> [!NOTE]  
>  Este tema contiene información específica del controlador ODBC de Visual FoxPro. Para obtener información general acerca de esta función, vea el tema correspondiente en [referencia de la API de ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Soporte técnico: completo  
  
 Ajuste de la API de ODBC: Nivel 1  
  
 Devuelve información acerca de los tipos de datos admitidos por un origen de datos. El controlador devuelve la información en un conjunto de resultados SQL. En la tabla siguiente se enumera los tipos de datos ODBC y el tipo de datos de Visual FoxPro correspondiente.  
  
|Tipo de ODBC|Tipo de objeto Visual FoxPro|  
|---------------|------------------------|  
|SQL_BIGINT|No compatible. No hay ningún tipo de Visual FoxPro de 64 bits.|  
|SQL_BIT|Lógico|  
|SQL_CHAR|Carácter|  
|SQL_DATE|Date|  
|SQL_DECIMAL|Numérico|  
|SQL_DOUBLE|Doble|  
|SQL_FLOAT|Doble|  
|SQL_INTEGER|Integer|  
|SQL_LONGVARBINARY|Memo (binario)|  
|SQL_LONGVARCHAR|Memorándum|  
|SQL_NUMERIC|Numérico *, moneda, Float|  
|SQL_REAL|Doble|  
|SQL_SMALLINT|Integer|  
|SQL_TIME|No compatible. No hay ningún Visual FoxPro *tiempo* tipo.|  
|SQL_TIMESTAMP|DateTime|  
|SQL_TINYINT|Integer|  
|SQL_VARBINARY|Memo (binario) *, General|  
|SQL_VARCHAR|Carácter|  
  
 * Tipo predeterminado  
  
 Para obtener más información acerca de los tipos de datos de Visual FoxPro, consulte [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md). Para obtener más información acerca de esta función, consulte [SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md) en el *referencia del programador de ODBC*.
