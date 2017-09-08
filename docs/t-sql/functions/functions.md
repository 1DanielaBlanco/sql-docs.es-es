---
title: "¿Cuáles son las funciones de base de datos de SQL de Microsoft? | Microsoft Docs"
ms.custom: 
ms.date: 06/28/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- built-in functions [SQL Server]
- function [SQL Server] See functions [SQL Server]
- functions [Transact-SQL]
- functions [SQL Server], about functions
- scalar functions
- functions [SQL Server]
ms.assetid: 17186213-5ab5-40b0-b470-b660af1ec44c
caps.latest.revision: 38
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 53a2a1be1099b2224b14f8c8d856b7ae07d42ac6
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="what-are-the-sql-database-functions"></a>¿Cuáles son las funciones de base de datos SQL?
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

Obtenga información acerca de las categorías de funciones integradas que puede utilizar con bases de datos SQL. Puede utilizar las funciones integradas o crear sus propias funciones definidas por el usuario.
  
## <a name="aggregate-functions"></a>Funciones de agregado

Las funciones de agregado realizan un cálculo sobre un conjunto de valores y devuelven un solo valor. Se permiten en la lista de selección o la cláusula HAVING de una instrucción SELECT. Puede utilizar una agregación en combinación con la cláusula GROUP BY para calcular la agregación en categorías de filas. Utilice la cláusula OVER para calcular la agregación en un intervalo específico de valor. La cláusula OVER no puede seguir las agregaciones GROUPING o GROUPING_ID.

Todas las funciones agregadas son deterministas, lo que significa que siempre devuelven el mismo valor cuando se ejecutan en los mismos valores de entrada. Para obtener más información, consulte [Deterministic and Nondeterministic Functions](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md). |

## <a name="analytic-functions"></a>Funciones analíticas
Las funciones analíticas calculan un valor agregado basándose en un grupo de filas. Sin embargo, a diferencia de las funciones de agregado, funciones analíticas pueden devolver varias filas para cada grupo. Puede utilizar funciones analíticas para calcular medias móviles, totales acumulados, porcentajes, o resultados de N superiores dentro de un grupo.

## <a name="ranking-functions"></a>Funciones de categoría
Las funciones de categoría devuelven un valor de categoría para cada fila de una partición. Según la función que se utilice, algunas filas pueden recibir el mismo valor que otras. Las funciones de categoría son no deterministas.

## <a name="rowset-functions"></a>Funciones de conjunto de filas
Funciones de conjunto de filas devuelven un objeto que se puede utilizar como referencias de tabla en una instrucción SQL.

## <a name="scalar-functions"></a>Funciones escalares
Operan sobre un valor y después devuelven otro valor. Las funciones escalares se pueden utilizar donde la expresión sea válida.

### <a name="categories-of-scalar-functions"></a>Categorías de funciones escalares
  
|Categoría de la función|Description|  
|-----------------------|-----------------|  
|[Funciones de configuración](configuration-functions-transact-sql.md)|Devuelven información acerca de la configuración actual.|  
|[Funciones de conversión](conversion-functions-transact-sql.md)|Admiten conversión y conversión de tipos de datos.|  
|[Funciones del cursor](cursor-functions-transact-sql.md)|Devuelven información acerca de los cursores.|  
|[Datos de fecha y hora tipos y funciones](date-and-time-data-types-and-functions-transact-sql.md)|Llevan a cabo operaciones sobre un valor de entrada de fecha y hora, y devuelven un valor numérico, de cadena o de fecha y hora.|  
|[Funciones JSON](json-functions-transact-sql.md)|Validar, consultar o cambiar datos JSON.|  
|[Funciones lógicas](http://msdn.microsoft.com/library/5b2b4546-951b-462d-91d5-e41fc5acd6f9)|Realizan operaciones lógicas.|  
|[Funciones matemáticas](mathematical-functions-transact-sql.md)|Realizan cálculos basados en valores de entrada proporcionados como parámetros a las funciones y devuelven valores numéricos.|  
|[Funciones de metadatos](metadata-functions-transact-sql.md)|Devuelven información acerca de la base de datos y los objetos de la base de datos.|  
|[Funciones de seguridad](security-functions-transact-sql.md)|Devuelven información acerca de usuarios y roles.|  
|[Funciones de cadena](string-functions-transact-sql.md)|Realizar operaciones en una cadena (**char** o **varchar**) valor de entrada y devuelve un valor de cadena o numérica.|  
|[Funciones del sistema](../../relational-databases/system-functions/system-functions-for-transact-sql.md)|Realizan operaciones y devuelven información acerca de valores, objetos y configuraciones de una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Funciones estadísticas del sistema](system-statistical-functions-transact-sql.md)|Devuelven información estadística acerca del sistema.|  
|[Funciones de imagen y texto](http://msdn.microsoft.com/library/b9c70488-1bf5-4068-a003-e548ccbc5199)|Realizan operaciones sobre los valores de entrada o columnas de texto o imagen, y devuelven información acerca del valor.|  
  
## <a name="function-determinism"></a>Determinismo de función  
 Las funciones integradas de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] son deterministas o no deterministas. Las funciones son deterministas cuando devuelven siempre el mismo resultado cada vez que se llaman con un conjunto específico de valores de entrada. Las funciones son no deterministas cuando es posible que devuelvan distintos resultados cada vez que se llaman con un mismo conjunto específico de valores de entrada. Para obtener más información, vea [funciones deterministas y no deterministas](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md)  
  
## <a name="function-collation"></a>Intercalación de funciones  
 Las funciones que toman una entrada de cadena de caracteres y devuelven una salida de cadena de caracteres utilizan la intercalación de la cadena de entrada para la salida.  
  
 Las funciones que toman entradas que no son de caracteres y devuelven una cadena de caracteres utilizan la intercalación predeterminada de la base de datos actual para la salida.  
  
 Las funciones que toman varias entradas de cadena de caracteres y devuelven una cadena de caracteres utilizan las reglas de prioridad de intercalación para establecer la intercalación de la cadena de salida. Para obtener más información, vea [prioridad de intercalación &#40; Transact-SQL &#41; ](../../t-sql/statements/collation-precedence-transact-sql.md).  
  
## <a name="see-also"></a>Vea también  
 [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md)   
 [Funciones deterministas y no deterministas](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md)   
 [Mediante los procedimientos almacenados &#40; MDX &#41;](../../mdx/using-stored-procedures-mdx.md)  
  
  
