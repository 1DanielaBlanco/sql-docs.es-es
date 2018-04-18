---
title: SQLStatistics (controlador de archivo de texto) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text file driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Text File Driver
ms.assetid: 311afc01-d656-425f-be43-4a8e7cbc9a97
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 162eb8302416664a65ddc767e817dfe70ae932a6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="sqlstatistics-text-file-driver"></a>SQLStatistics (controlador de archivo de texto)
> [!NOTE]  
>  En este tema se proporciona información específica del controlador de archivo de texto. Para obtener información general acerca de esta función, vea el tema correspondiente en [referencia de la API de ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Columna|Comentarios|  
|------------|--------------|  
|TABLE_QUALIFIER|La ruta de acceso a un directorio.<br /><br /> No se admite la coincidencia de patrones en los *szTableQualifier* argumento.|  
|TABLE_OWNER|Se devuelve NULL en esta columna porque no se admite el nombre del propietario.|  
|TABLE_NAME|Nombre de la tabla no delimitado.<br /><br /> No se admite la coincidencia de patrones en los *szTableName* argumento.|  
|INDEX_QUALIFIER|Siempre devuelve NULL.|  
|INDEX_NAME|Dependientes del índice.|  
|TYPE|Se devolverá solo SQL_TABLE_STAT o SQL_INDEX_OTHER para el tipo.|  
|SEQ_IN_INDEX|Dependientes del índice.|  
|COLUMN_NAME|Dependientes del índice.|  
|COLLATION|Dependientes del índice.|  
|PAGES|Siempre devuelve NULL.|  
  
 El filtrado se basa en unicidad (la *fUnique* argumento). El *fAccuracy* parámetro se ignora.
