---
title: Vs ha iniciado. Modificaciones registradas | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-text-image-columns
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- logged vs. nonlogged modifications [SQL Server Native Client]
- columns [ODBC]
- ODBC data types, image columns
- nonlogged vs. logged modifications
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 20aa5b27-4a2c-46e7-8356-beb0eebf4b7e
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4cf91e1b77d1d6731d73653682320e1c61eec734
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="logged-vs-unlogged-modifications"></a>Vs ha iniciado. Modificaciones registradas
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Una aplicación puede solicitar que el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] controlador ODBC Native Client no registre **texto**, **ntext**, y **imagen** modificaciones. Sin embargo, se debe tener cautela con esta opción. Debe usarse solo para aquellas situaciones donde la **texto**, **ntext**, o **imagen** datos no son críticos y los propietarios de datos están dispuestos a compensar la capacidad para recuperar datos mayor rendimiento.  
  
 El registro de **texto**, **ntext**, y **imagen** modificaciones se controla mediante una llamada a [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) con el  *Atributo* parámetro establecido en SQL_SOPT_SS_ TEXTPTR_LOGGING y *ValuePtr* establecido en SQL_TL_ON o SQL_TL_OFF.  
  
## <a name="see-also"></a>Vea también  
 [Administrar columnas de texto e imagen](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  
