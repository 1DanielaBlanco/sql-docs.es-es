---
title: SQLTables (controlador ODBC de Visual FoxPro) | Documentos de Microsoft
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
- SQLTables function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 69e2a038-5def-423f-91aa-8756e069dd2a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e8eccd686c1c4e3226a929cb39ee16e1921435ca
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="sqltables-visual-foxpro-odbc-driver"></a>SQLTables (controlador ODBC de Visual FoxPro)
> [!NOTE]  
>  Este tema contiene información específica del controlador ODBC de Visual FoxPro. Para obtener información general acerca de esta función, vea el tema correspondiente en [referencia de la API de ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Soporte técnico: completo  
  
 Ajuste de la API de ODBC: Nivel 1  
  
 Devuelve la lista de nombres de tabla especificado por el parámetro en el **SQLTables** instrucción. Si no se especifica ningún parámetro, devuelve los nombres de tabla que se almacenan en el origen de datos actual. El controlador devuelve la información como un conjunto de resultados.  
  
 Llamadas de tipo de enumeración no reciben una entrada de conjunto de resultados para las vistas remotas ni vistas con parámetros locales. Sin embargo, una llamada a **SQLTables** con una tabla única especificador de nombre encontrar una coincidencia para una vista de este tipo si está presente con ese nombre, lo que permite la API que se usará para comprobar si hay conflictos de nombre antes de la creación de una nueva tabla.  
  
> [!NOTE]  
>  Marca la diferencia entre el controlador ODBC de Visual FoxPro [tablas de base de datos](../../odbc/microsoft/visual-foxpro-terminology.md) y [libre tablas](../../odbc/microsoft/visual-foxpro-terminology.md), incluso cuando ambos tipos de tablas se almacenan en el mismo directorio en el sistema. Si el origen de datos es un directorio de tablas libres, el controlador ODBC de Visual FoxPro no catálogo o devolver los nombres de las tablas que están asociados a una base de datos.  
  
 Para obtener más información, consulte [SQLTables](../../odbc/reference/syntax/sqltables-function.md) en el *referencia del programador de ODBC*.
