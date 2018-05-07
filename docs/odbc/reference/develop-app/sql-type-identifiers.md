---
title: Los identificadores de tipo SQL | Documentos de Microsoft
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
- data types [ODBC], identifiers
- SQL data types [ODBC], identifiers
- type identifiers [ODBC], SQL
- identifiers [ODBC], SQL type
- SQL type identifiers [ODBC]
ms.assetid: 22f6793b-2f43-4281-b35a-28f48e504dd8
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f3a9270e698f7f0ff12bd12c02de865a3c6f2b3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="sql-type-identifiers"></a>Identificadores de tipo SQL
Cada origen de datos define sus propios tipos de datos SQL. ODBC define los identificadores de tipo y describe las características generales de los tipos de datos SQL que se podrían asignar a cada identificador de tipo. Es específica del controlador cómo cada tipo de datos en el origen de datos subyacente se asigna a un identificador de tipo SQL de ODBC.  
  
 Por ejemplo, SQL_CHAR es el identificador de tipo para una columna de caracteres con una longitud fija, normalmente entre 1 y 254 caracteres. Estas características se corresponden con el tipo de datos de carácter situado en muchos orígenes de datos SQL. Por lo tanto, cuando una aplicación detecta que el identificador de tipo para una columna es SQL_CHAR, puede asumir probablemente se trata de una columna CHAR. Sin embargo, debería comprobar la longitud de bytes de la columna antes de dar por supuesto que está entre 1 y 254 caracteres; el controlador para un origen de datos no son de SQL, por ejemplo, puede asignar una columna de caracteres de longitud fija de 500 caracteres a SQL_CHAR o SQL_LONGVARCHAR, porque ninguna de ellas es una coincidencia exacta.  
  
 ODBC define una amplia variedad de identificadores de tipo SQL. Sin embargo, el controlador no tiene que todas las de estos identificadores usar. En su lugar, usa solo esos identificadores que necesita para exponer los tipos de datos SQL admite el origen de datos subyacente. Si el origen de datos subyacente admite tipos de datos SQL para que ningún identificador de tipo correspondiente, el controlador puede definir los identificadores de tipo adicionales. Para obtener más información, consulte [tipos de datos específicos del controlador, Descriptor de tipos, información de tipos, tipos de diagnóstico y atributos](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Para obtener una descripción completa de los identificadores de tipo SQL, vea [tipos de datos C](../../../odbc/reference/appendixes/c-data-types.md) en tipos de datos de apéndice D:.
