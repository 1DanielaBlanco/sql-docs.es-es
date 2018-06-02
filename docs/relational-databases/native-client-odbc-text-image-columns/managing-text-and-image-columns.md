---
title: Administrar columnas Text e Image | Documentos de Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-text-image-columns
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- data types [ODBC], mapping
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 7b543556-ff36-4d35-ac08-de96223d92cd
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 300caa16e74ee36e740c901a295c1c30c1723d33
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34707243"
---
# <a name="managing-text-and-image-columns"></a>Administrar columnas de texto e imagen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **texto**, **ntext**, y **imagen** datos (también denominados datos largos) son caracteres o tipos de datos de cadena binaria que pueden contener valores de datos demasiado grande para caber en **char**, **varchar**, **binario**, o **varbinary** columnas. El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **texto** tipo de datos asigna al tipo de datos ODBC SQL_LONGVARCHAR; **ntext** se asigna a SQL_WLONGVARCHAR y **imagen** a SQL_LONGVARBINARY. Es posible que algunos elementos de datos, como documentos largos o mapas de bits grandes, resulten demasiado grandes para poder almacenarlos correctamente en la memoria. Al recuperar datos long de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en partes secuenciales, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] controlador ODBC Native Client permite a una aplicación llamar a [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md). Para enviar datos largos en partes secuenciales, la aplicación puede llamar a [SQLPutData](../../relational-databases/native-client-odbc-api/sqlputdata.md). Los parámetros para los que se envían datos durante la ejecución se conocen como parámetros de datos en ejecución.  
  
 Una aplicación puede escribir o recuperar cualquier tipo de datos (no solo datos largos) con realmente **SQLPutData** o **SQLGetData**, aunque solo **caracteres** y  **binario** datos se pueden enviar o recuperar en partes. Sin embargo, si los datos son lo suficientemente pequeños como para caber en un único búfer, no suele haber motivo para utilizar **SQLPutData** o **SQLGetData**. Resulta mucho más fácil enlazar el búfer único al parámetro o columna.  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [Texto delimitado frente a texto sin delimitar y columnas de imagen](../../relational-databases/native-client-odbc-text-image-columns/bound-vs-unbound-text-and-image-columns.md)  
  
-   [Modificaciones registradas frente a modificaciones no registradas](../../relational-databases/native-client-odbc-text-image-columns/logged-vs-unlogged-modifications.md)  
  
-   [Datos en ejecución y columnas de tipo text, ntext o image](../../relational-databases/native-client-odbc-text-image-columns/data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>Vea también  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
