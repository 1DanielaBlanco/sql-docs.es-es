---
title: Comando de ruta de acceso SET | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
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
- SET PATH command [ODBC]
ms.assetid: db488d1e-0963-4f45-8c76-a23b9bde9e9d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 553c3f464b5a14d578aa05bece939126f7251974
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="set-path-command"></a>Comando de ruta de acceso set.
Especifica una ruta de acceso para las búsquedas de archivos. Para obtener información específica del controlador, vea la sección Comentarios.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
SET PATH TO [Path]  
```  
  
## <a name="arguments"></a>Argumentos  
 A [ *ruta de acceso*]  
 Especifica los directorios que desee buscar de Visual FoxPro. Use comas o punto y coma para separar los directorios.  
  
## <a name="remarks"></a>Comentarios  
 Establecer ruta de acceso permite especificar las rutas de acceso de búsqueda para otros programas de Visual FoxPro que pueden llamar a procedimientos almacenados. Establecer ruta de acceso no cambiará la ruta de acceso del origen de datos que ha especificado para la conexión.  
  
 Emitir establecer ruta de acceso a sin *ruta de acceso* para restaurar la ruta de acceso a la carpeta o el directorio predeterminado.  
  
## <a name="driver-remarks"></a>Comentarios del controlador  
 Si emite SET PATH en un procedimiento almacenado, se omitirán mediante los comandos y las funciones siguientes:  
  
-   Las funciones de catálogo como [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md) y [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) omitirá la nueva ruta de acceso y continuar hacer referencia a la ruta de acceso especificada por el origen de datos en [SQLPrepare](../../odbc/microsoft/sqlprepare-visual-foxpro-odbc-driver.md) o [ SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
-   Comandos como SELECT, INSERT, UPDATE, DELETE y CREATE TABLE omitirá la nueva ruta de acceso y continuar hacer referencia a la ruta de acceso especificada por el origen de datos en **SQLPrepare** o **SQLExecDirect**.  
  
 Si debe emitir establecer ruta de acceso en un procedimiento almacenado y posteriormente no establece la ruta de acceso a su estado original, otra conexión con la base de datos utilizará la nueva ruta de acceso (porque no tiene un ámbito establecer ruta de acceso a las sesiones de datos).  
  
 Si desea crear, seleccionar o actualizar las tablas en un directorio distinto del especificado por el origen de datos, especifique la ruta de acceso completa del archivo con el comando.  
  
## <a name="see-also"></a>Vea también  
 [Cuadro de diálogo de configuración de Visual FoxPro ODBC](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)   
 [SQLColumns (controlador ODBC de Visual FoxPro)](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)   
 [SQLDriverConnect (controlador ODBC de Visual FoxPro)](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)   
 [SQLTables (controlador ODBC de Visual FoxPro)](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)
