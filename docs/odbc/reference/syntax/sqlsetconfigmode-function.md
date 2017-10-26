---
title: "Función SQLSetConfigMode | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLSetConfigMode
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConfigMode
helpviewer_keywords:
- SQLSetConfigMode function [ODBC]
ms.assetid: 09eb88ea-b6f6-4eca-b19d-0951cebc6c0a
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c8919f758c486e6569b9620fcaa7bcf76f4dac0f
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetconfigmode-function"></a>SQLSetConfigMode (función)
**Conformidad**  
 Versión introdujo: ODBC 3.0  
  
 **Resumen**  
 **SQLSetConfigMode** establece el modo de configuración que indica que la entrada de Odbc.ini enumerar valores DSN en la información del sistema.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
BOOL SQLSetConfigMode(  
     UWORD     wConfigMode);  
```  
  
## <a name="arguments"></a>Argumentos  
 *wConfigMode*  
 [Entrada] El modo de configuración de instalador (vea "Comentarios"). El valor de *wConfigMode* puede ser:  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Devuelve  
 La función devuelve TRUE si se realiza correctamente, FALSE si se produce un error.  
  
## <a name="diagnostics"></a>Diagnósticos  
 Cuando **SQLSetConfigMode** devuelve FALSE, un asociado * \*pfErrorCode* valor puede obtenerse mediante una llamada a **SQLInstallerError**. La siguiente tabla se recogen los * \*pfErrorCode* valores que pueden ser devueltos por **SQLInstallerError** y se explica cada uno de ellos en el contexto de esta función.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Secuencia de parámetros no válidos|El *wConfigMode* argumento no contenía ODBC_USER_DSN, ODBC_SYSTEM_DSN o ODBC_BOTH_DSN.|  
  
## <a name="comments"></a>Comentarios  
 Esta función se usa para establecer la entrada Odbc.ini enumerar valores DSN se encuentra en la información del sistema. Si *wConfigMode* es ODBC_USER_DSN, el DSN es un DSN de usuario y la función lee de la entrada Odbc.ini en HKEY_CURRENT_USER. Si es ODBC_SYSTEM_DSN, el DSN es un DSN de sistema y la función lee de la entrada Odbc.ini en HKEY_LOCAL_MACHINE. Si es ODBC_BOTH_DSN, se prueba con HKEY_CURRENT_USER, y si se produce un error, a continuación, se utiliza HKEY_LOCAL_MACHINE.  
  
 Esta función no afecta a **SQLCreateDataSource** y **SQLDriverConnect**. El modo de configuración debe establecerse cuando un controlador lee desde el registro mediante una llamada a **SQLGetPrivateProfileString** o escribe en el registro mediante una llamada a **SQLWritePrivateProfileString**. Las llamadas a **SQLGetPrivateProfileString** y **SQLWritePrivateProfileString** utilizan el modo de configuración para saber qué parte del registro para operar en.  
  
> [!CAUTION]  
>  **SQLSetConfigMode** debe llamarse solo cuando sea necesario; si el modo está establecido de forma incorrecta, puede producir un error en el programa de instalación de ODBC funcionar correctamente.  
  
 **SQLSetConfigMode** realiza una modificación directa del registro del modo de configuración. Esto es aparte del proceso de modificar el modo de configuración mediante una llamada a **SQLConfigDataSource**. Una llamada a **SQLConfigDataSource** establece el modo de configuración para distinguir los DSN de sistema y de usuario cuando se modifica un DSN. Antes de devolver, **SQLConfigDataSource** restablece el modo de configuración a BOTHDSN.  
  
## <a name="related-functions"></a>Funciones relacionadas  
  
|Para obtener información acerca de|Vea|  
|---------------------------|---------|  
|Crear un origen de datos|[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|  
|Conectarse a un origen de datos mediante un cuadro de diálogo o la cadena de conexión|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Recuperar el modo de configuración|[SQLGetConfigMode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|

