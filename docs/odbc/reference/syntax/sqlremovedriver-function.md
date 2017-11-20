---
title: "Función SQLRemoveDriver | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLRemoveDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDriver
helpviewer_keywords:
- SQLRemoveDriver function [ODBC]
ms.assetid: 9a3b4f8b-982b-44b9-ade6-754ff026dc90
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d191f3ce9d30d241c4d4d37d9961a590ae33817b
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="sqlremovedriver-function"></a>SQLRemoveDriver (función)
**Conformidad**  
 Versión introdujo: ODBC 3.0  
  
 **Resumen**  
 **SQLRemoveDriver** cambia o quita la información sobre el controlador de la entrada de Odbcinst.ini en la información del sistema.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
BOOL SQLRemoveDriver(  
     LPCSTR   lpszDriver,  
     BOOL     fRemoveDSN,  
     LPDWORD  lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Argumentos  
 *lpszDriver*  
 [Entrada] El nombre del controlador como está registrado en la clave de Odbcinst.ini de la información del sistema.  
  
 *fRemoveDSN*  
 [Entrada] Los valores válidos son:  
  
 TRUE: Quitar DSN asociado con el controlador especificado en *lpszDriver*. FALSE: No quite DSN asociado con el controlador especificado en *lpszDriver*.  
  
 *lpdwUsageCount*  
 [Salida] El contador de uso del controlador después de llamar a esta función.  
  
## <a name="returns"></a>Devuelve  
 La función devuelve TRUE si se realiza correctamente, FALSE si se produce un error. Si no existe ninguna entrada en la información del sistema cuando se llama a esta función, la función devuelve FALSE.  
  
## <a name="diagnostics"></a>Diagnósticos  
 Cuando **SQLRemoveDriver** devuelve FALSE, un asociado  *\*pfErrorCode* valor puede obtenerse mediante una llamada a **SQLInstallerError**. La siguiente tabla se recogen los  *\*pfErrorCode* valores que pueden ser devueltos por **SQLInstallerError** y se explica cada uno de ellos en el contexto de esta función.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Error del instalador general|Se produjo un error para que no se produjo ningún error de instalación concreto.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|No se encuentra en el registro de componente|El programa de instalación no pudo quitar la información del controlador porque no existía en el registro o no se encontró en el registro.|  
|ODBC_ERROR_INVALID_NAME|Nombre de traductor o controlador no válido|El *lpszDriver* argumento no era válido.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|No se pudo incrementar o disminuir el recuento de uso de componente|El instalador no pudo reducir el recuento de uso del controlador.|  
|ODBC_ERROR_REQUEST_FAILED|Error en la solicitud|El *fRemoveDSN* argumento era TRUE; sin embargo, no se pudieron quitar uno o más DSN. La llamada a **SQLConfigDriver** con la solicitud ODBC_REMOVE_DRIVER generado un error.|  
|ODBC_ERROR_OUT_OF_MEM|No hay memoria suficiente|El programa de instalación no pudo realizar la función debido a la falta de memoria.|  
  
## <a name="comments"></a>Comentarios  
 **SQLRemoveDriver** complementa el [SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md) función y las actualizaciones de contar el uso del componente en la información del sistema. Esta función se debería llamar solo desde una aplicación de instalación.  
  
 **SQLRemoveDriver** disminuye el valor de recuento de uso de componente en 1. Si el recuento de uso de componente llega a 0, se producirá lo siguiente:  
  
1.  El **SQLConfigDriver** se llamará a la función con la opción ODBC_REMOVE_DRIVER. Si el *fRemoveDSN* opción está establecida en TRUE, el **ConfigDSN** llamadas a funciones **SQLRemoveDSNFromIni** para quitar todos los orígenes de datos asociados con el controlador especificado en *lpszDriver.* Si el *fRemoveDSN* opción está establecida en FALSE, no se eliminarán los orígenes de datos.  
  
2.  La entrada del controlador en la información del sistema que se va a quitar. La entrada del controlador está en la siguiente ubicación de información de sistema, en el nombre del controlador:  
  
     `HKEY_LOCAL_MACHINE`  
  
     `SOFTWARE`  
  
     `ODBC`  
  
     `Odbcinst.ini`  
  
 **SQLRemoveDriver** realmente no elimina los archivos. El programa de llamada es responsable de eliminar los archivos y mantiene el recuento de uso de archivos. Solo una vez han alcanzado el recuento de utilización del componente y el recuento de uso de archivo cero es un archivo físicamente eliminado. Se pueden eliminar algunos archivos en un componente y otros usuarios eliminan no, dependiendo de si los archivos se usan para otras aplicaciones que se incrementan el contador de uso de archivo.  
  
 **SQLRemoveDriver** también se llama como parte de un proceso de actualización. Si una aplicación detecta que tiene que realizar una actualización y previamente instaló al controlador, se debe quitar y volver a instalar el controlador. **SQLRemoveDriver** en primer lugar debe llamarse para disminuir el recuento de uso del componente y, a continuación, **SQLInstallDriverEx** debe llamarse para incrementar el contador de uso del componente. El programa de instalación de la aplicación debe reemplazar los archivos antiguos con los nuevos archivos. El contador de uso de archivo seguirá siendo el mismo, y otras aplicaciones que usan los archivos de versiones anteriores ahora usará la versión más reciente.  
  
## <a name="related-functions"></a>Funciones relacionadas  
  
|Para obtener información acerca de|Vea|  
|---------------------------|---------|  
|Agregar, modificar o quitar un controlador|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md) (en la configuración del archivo DLL)|  
|Agregar, modificar o quitar un controlador|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|  
|Instalar un controlador|[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|

