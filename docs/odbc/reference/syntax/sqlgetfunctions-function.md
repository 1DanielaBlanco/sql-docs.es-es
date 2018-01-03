---
title: "Función SQLGetFunctions | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLGetFunctions
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLGetFunctions
helpviewer_keywords: SQLGetFunctions function [ODBC]
ms.assetid: 0451d2f9-0f4f-46ba-b252-670956a52183
caps.latest.revision: "23"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9a38bc5d8e071efee286f726d75f6949243cbb77
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetfunctions-function"></a>Función SQLGetFunctions
**Conformidad**  
 Versión introdujo: Cumplimiento de estándares 1.0 de ODBC: ISO 92  
  
 **Resumen**  
 **SQLGetFunctions** devuelve información acerca de si un controlador es compatible con una determinada función ODBC. Esta función se implementa en el Administrador de controladores; También puede implementarse en los controladores. Si implementa un controlador **SQLGetFunctions**, el Administrador de controladores llama a la función en el controlador. De lo contrario, ejecuta la propia función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
SQLRETURN SQLGetFunctions(  
     SQLHDBC           ConnectionHandle,  
     SQLUSMALLINT      FunctionId,  
     SQLUSMALLINT *    SupportedPtr);  
```  
  
## <a name="arguments"></a>Argumentos  
 *IdentificadorConexión*  
 [Entrada] Identificador de conexión.  
  
 *FunctionId*  
 [Entrada] A **#define** valor que identifica la función ODBC de interés; **SQL_API_ODBC3_ALL_FUNCTIONS orSQL_API_ALL_FUNCTIONS**. **SQL_API_ODBC3_ALL_FUNCTIONS** utilizado por una aplicación ODBC 3*.x* aplicación para determinar la compatibilidad con ODBC 3*.x* y funciones anteriores. **SQL_API_ALL_FUNCTIONS** utiliza una API ODBC 2*.x* aplicación para determinar la compatibilidad de ODBC 2*.x* y funciones anteriores.  
  
 Para obtener una lista de **#define** valores que identifican las funciones ODBC, consulte las tablas en "Comentarios".  
  
 *SupportedPtr*  
 [Salida]  Si *FunctionId* identifica una única función ODBC, *SupportedPtr* señala a una sola SQLUSMALLINT valor que es SQL_TRUE si se admite la función especificada por el controlador y SQL_FALSE si no lo es admite.  
  
 Si *FunctionId* es SQL_API_ODBC3_ALL_FUNCTIONS, *SupportedPtr* apunta a una matriz SQLSMALLINT con un número de elementos iguales a SQL_API_ODBC3_ALL_FUNCTIONS_SIZE. Esta matriz se trata por el Administrador de controladores como un mapa de bits de 4.000 bits que puede utilizarse para determinar si una aplicación ODBC 3*.x* o se admite la función anterior. La macro SQL_FUNC_EXISTS se invoca para determinar la compatibilidad con la función. (Vea "Comentarios".) Una aplicación ODBC 3*.x* aplicación puede llamar a **SQLGetFunctions** con SQL_API_ODBC3_ALL_FUNCTIONS contra un ODBC 3*.x* o 2 de ODBC*.x* controlador.  
  
 Si *FunctionId* es SQL_API_ALL_FUNCTIONS, *SupportedPtr* señala a una matriz SQLUSMALLINT de 100 elementos. La matriz se indiza por **#define** valores utilizados por *FunctionId* para identificar cada función ODBC; algunos de los elementos de la matriz se reserva para uso futuro y no utilizados. Un elemento es SQL_TRUE si se identifica un ODBC 2*.x* o función earlier compatibles con el controlador. Si se identifica una función ODBC no admitida el controlador o no identifica una función ODBC es SQL_FALSE.  
  
 Las matrices devueltas en **SupportedPtr* usar indización de base cero.  
  
## <a name="returns"></a>Devuelve  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnósticos  
 Cuando **SQLGetFunctions** devuelve SQL_ERROR o SQL_SUCCESS_WITH_INFO, un valor SQLSTATE asociado se puede obtener mediante una llamada a **SQLGetDiagRec** con un *HandleType* de SQL_HANDLE_DBC y un *controlar* de *IdentificadorConexión*. En la tabla siguiente se enumera los valores SQLSTATE devueltos normalmente por **SQLGetFunctions** y se explica cada uno de ellos en el contexto de esta función; la notación "(DM)" precede a las descripciones de SQLSTATE devuelto por el Administrador de controladores. El código de retorno asociado a cada valor SQLSTATE es SQL_ERROR, a menos que se indique lo contrario.  
  
|SQLSTATE|Error|Description|  
|--------|-----|-----------|  
|01000|Advertencia general|Mensaje informativo de específicas del controlador. (La función devuelve SQL_SUCCESS_WITH_INFO).|  
|08S01|Error de vínculo de comunicación|El vínculo de comunicación entre el controlador y el origen de datos al que se conectó el controlador no pudo antes del procesamiento de la función se ha completado.|  
|HY000|Error general|Se produjo un error para que no hubo ninguna SQLSTATE específico y para el que se ha definido ningún SQLSTATE específico de la implementación. El mensaje de error devuelto por **SQLGetDiagRec** en el  *\*MessageText* búfer describe el error y su causa.|  
|HY001|Error de asignación de memoria|El controlador no pudo asignar la memoria necesaria para admitir la ejecución o la finalización de la función.|  
|HY010|Error de secuencia de función|(DM) **SQLGetFunctions** se llamó antes de **SQLConnect**, **SQLBrowseConnect**, o **SQLDriverConnect**.<br /><br /> (DM) **SQLBrowseConnect** se llamó para el *IdentificadorConexión* y devuelve SQL_NEED_DATA. Esta función se invoca antes de **SQLBrowseConnect** devuelve SQL_SUCCESS_WITH_INFO o SQL_SUCCESS.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, o **SQLMoreResults** se llamó para el *IdentificadorConexión* devolvió SQL_PARAM_DATA_ ESTÁ DISPONIBLE. Esta función se invoca antes de que se recuperan los datos para todos los parámetros transmitidos.|  
|HY013|Error de administración de memoria|No se pudo procesar la llamada de función porque los objetos subyacentes de la memoria no se pudieron tener acceso, posiblemente debido a condiciones de memoria insuficiente.|  
|HY095|Tipo de función fuera del intervalo|(DM) no válido *FunctionId* se especificó un valor.|  
|HY117|Se suspende la conexión debido al estado de transacción desconocido. Solo se desconecte y se permiten las funciones de solo lectura.|(DM) para obtener más información sobre el estado suspendido, consulte [función SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Tiempo de espera de conexión expirado|El período de tiempo de espera de conexión finalizó antes de que el origen de datos se respondió a la solicitud. El período de tiempo de espera de conexión se establece a través de **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
  
## <a name="comments"></a>Comentarios  
 **SQLGetFunctions** siempre devuelve que **SQLGetFunctions**, **SQLDataSources**, y **SQLDrivers** son compatibles. Esto consigue porque estas funciones se implementan en el Administrador de controladores. El Administrador de controladores se asignará una función de ANSI para la función Unicode correspondiente si la función Unicode existe y asignará una función de Unicode a la función ANSI correspondiente si existe la función ANSI. Para obtener información acerca de cómo utilizan aplicaciones **SQLGetFunctions**, consulte [niveles de cumplimiento de la interfaz](../../../odbc/reference/develop-app/interface-conformance-levels.md).  
  
 La siguiente es una lista de valores válidos para *FunctionId* para las funciones que se ajustan al nivel de cumplimiento de normas: ISO 92:  
  
|Valor de FunctionId|Valor de FunctionId|  
|----------|----------|  
|SQL_API_SQLALLOCHANDLE|SQL_API_SQLGETDESCFIELD|  
|SQL_API_SQLBINDCOL|SQL_API_SQLGETDESCREC|  
|SQL_API_SQLCANCEL|SQL_API_SQLGETDIAGFIELD|  
|SQL_API_SQLCLOSECURSOR|SQL_API_SQLGETDIAGREC|  
|SQL_API_SQLCOLATTRIBUTE|SQL_API_SQLGETENVATTR|  
|SQL_API_SQLCONNECT|SQL_API_SQLGETFUNCTIONS|  
|SQL_API_SQLCOPYDESC|SQL_API_SQLGETINFO|  
|SQL_API_SQLDATASOURCES|SQL_API_SQLGETSTMTATTR|  
|SQL_API_SQLDESCRIBECOL|SQL_API_SQLGETTYPEINFO|  
|SQL_API_SQLDISCONNECT|SQL_API_SQLNUMRESULTCOLS|  
|SQL_API_SQLDRIVERS|SQL_API_SQLPARAMDATA|  
|SQL_API_SQLENDTRAN|SQL_API_SQLPREPARE|  
|SQL_API_SQLEXECDIRECT|SQL_API_SQLPUTDATA|  
|SQL_API_SQLEXECUTE|SQL_API_SQLROWCOUNT|  
|SQL_API_SQLFETCH|SQL_API_SQLSETCONNECTATTR|  
|SQL_API_SQLFETCHSCROLL|SQL_API_SQLSETCURSORNAME|  
|SQL_API_SQLFREEHANDLE|SQL_API_SQLSETDESCFIELD|  
|SQL_API_SQLFREESTMT|SQL_API_SQLSETDESCREC|  
|SQL_API_SQLGETCONNECTATTR|SQL_API_SQLSETENVATTR|  
|SQL_API_SQLGETCURSORNAME|SQL_API_SQLSETSTMTATTR|  
|SQL_API_SQLGETDATA| |  
  
 La siguiente es una lista de valores válidos para *FunctionId* para las funciones que se ajuste al nivel de cumplimiento de normas – Open Group:  
  
|Valor de FunctionId|Valor de FunctionId|  
|-|-|  
|SQL_API_SQLCOLUMNS|SQL_API_SQLSTATISTICS|  
|SQL_API_SQLSPECIALCOLUMNS|SQL_API_SQLTABLES|  
  
 La siguiente es una lista de valores válidos para *FunctionId* para las funciones que cumplen el nivel de cumplimiento de normas: de ODBC.  
  
|Valor de FunctionId|Valor de FunctionId|  
|-|-|  
|SQL_API_SQLBINDPARAMETER|SQL_API_SQLNATIVESQL|  
|SQL_API_SQLBROWSECONNECT|SQL_API_SQLNUMPARAMS|  
|SQL_API_SQLBULKOPERATIONS [1]|SQL_API_SQLPRIMARYKEYS|  
|SQL_API_SQLCOLUMNPRIVILEGES|SQL_API_SQLPROCEDURECOLUMNS|  
|SQL_API_SQLDESCRIBEPARAM|SQL_API_SQLPROCEDURES|  
|SQL_API_SQLDRIVERCONNECT|SQL_API_SQLSETPOS|  
|SQL_API_SQLFOREIGNKEYS|SQL_API_SQLTABLEPRIVILEGES|  
|SQL_API_SQLMORERESULTS| |  
  
 [1] cuando se trabaja con una API ODBC 2*.x* controlador, **SQLBulkOperations** se devolverá como solo se admite si las dos opciones siguientes son verdaderas: la API ODBC 2*.x* controlador es compatible con  **SQLSetPos**, y el tipo de información SQL_POS_OPERATIONS devuelve el bit SQL_POS_ADD como conjunto.  
  
 La siguiente es una lista de valores válidos para *FunctionId* para funciones que se introdujeron en ODBC 3.8 o posterior:  
  
|Valor de FunctionId|  
|-|  
|SQL_API_SQLCANCELHANDLE [2]|  
  
 [2] **SQLCancelHandle** se devolverá como solo se admite si el controlador admite tanto **SQLCancel** y **SQLCancelHandle**. Si **SQLCancel** se admite pero **SQLCancelHandle** no lo es, la aplicación puede seguir llamando a **SQLCancelHandle** en un identificador de instrucción, ya que se va a asignar a  **SQLCancel**.  
  
## <a name="sqlfuncexists-macro"></a>SQL_FUNC_EXISTS (macro)  
 El SQL_FUNC_EXISTS (*SupportedPtr*, *FunctionID*) macro se usa para determinar la compatibilidad con ODBC 3*.x* o funciones anteriores después **SQLGetFunctions**  se ha llamado con un *FunctionId* argumento de SQL_API_ODBC3_ALL_FUNCTIONS. La aplicación llama a SQL_FUNC_EXISTS con el *SupportedPtr* establecido en el *SupportedPtr* pasa *SQLGetFunctions*y con el  *FunctionID* establecido en el **#define** para la función. SQL_FUNC_EXISTS devuelve SQL_TRUE si se admite la función y SQL_FALSE en caso contrario.  
  
> [!NOTE]  
>  Cuando se trabaja con una API ODBC 2*.x* controlador ODBC 3*.x* el Administrador de controladores devuelve SQL_TRUE para **SQLAllocHandle** y **SQLFreeHandle**porque **SQLAllocHandle** se asigna a **SQLAllocEnv**, **SQLAllocConnect**, o **SQLAllocStmt**, y Dado que **SQLFreeHandle** se asigna a **SQLFreeEnv**, **SQLFreeConnect**, o **SQLFreeStmt**. **SQLAllocHandle** o **SQLFreeHandle** con un *HandleType* de SQL_HANDLE_DESC no se admite, sin embargo, incluso si se devuelve SQL_TRUE para las funciones, porque no hay ninguna ODBC 2*.x* función que asigna a en este caso.  
  
## <a name="code-example"></a>Ejemplo de código  
 Los tres ejemplos siguientes muestran cómo una aplicación usa **SQLGetFunctions** para determinar si un controlador es compatible con **SQLTables**, **SQLColumns**, y  **SQLStatistics**. Si el controlador no admite estas funciones, la aplicación desconecta el controlador. El primer ejemplo se llama **SQLGetFunctions** una vez para cada función.  
  
```  
SQLUSMALLINT TablesExists, ColumnsExists, StatisticsExists;  
RETCODE retcodeTables, retcodeColumns, retcodeStatistics  
  
retcodeTables = SQLGetFunctions(hdbc, SQL_API_SQLTABLES, &TablesExists);  
retcodeColumns = SQLGetFunctions(hdbc, SQL_API_SQLCOLUMNS, &ColumnsExists);  
retcodeStatistics = SQLGetFunctions(hdbc, SQL_API_SQLSTATISTICS, &StatisticsExists);  
  
// SQLGetFunctions is completed successfully and SQLTables, SQLColumns, and SQLStatistics are supported by the driver.  
if (retcodeTables == SQL_SUCCESS && TablesExists == SQL_TRUE &&   
retcodeColumns == SQL_SUCCESS && ColumnsExists == SQL_TRUE &&   
retcodeStatistics == SQL_SUCCESS && StatisticsExists == SQL_TRUE)   
{  
  
   // Continue with application  
  
}  
  
SQLDisconnect(hdbc);  
```  
  
 En el segundo ejemplo, llama a una aplicación de ODBC 3.x **SQLGetFunctions** y pasa una matriz en la que **SQLGetFunctions** devuelve información acerca de todos los ODBC 3.x y funciones anteriores.  
  
```  
RETCODE retcodeTables, retcodeColumns, retcodeStatistics  
SQLUSMALLINT fExists[SQL_API_ODBC3_ALL_FUNCTIONS_SIZE];  
  
retcode = SQLGetFunctions(hdbc, SQL_API_ODBC3_ALL_FUNCTIONS, fExists);  
  
// SQLGetFunctions is completed successfully and SQLTables, SQLColumns, and SQLStatistics are supported by the driver.  
if (reccode == SQL_SUCCESS &&   
SQL_FUNC_EXISTS(fExists, SQL_API_SQLTABLES) == SQL_TRUE &&  
   SQL_FUNC_EXISTS(fExists, SQL_API_SQLCOLUMNS) == SQL_TRUE &&  
   SQL_FUNC_EXISTS(fExists, SQL_API_SQLSTATISTICS) == SQL_TRUE)   
{  
  
   // Continue with application  
  
}  
  
SQLDisconnect(hdbc);  
```  
  
 El tercer ejemplo es una aplicación de ODBC 2.x llama **SQLGetFunctions** y pasa una matriz de 100 elementos en la que **SQLGetFunctions** devuelve información acerca de todos los ODBC 2.x y funciones anteriores.  
  
```  
#define FUNCTIONS 100  
  
RETCODE retcodeTables, retcodeColumns, retcodeStatistics  
SQLUSMALLINT fExists[FUNCTIONS];  
  
retcode = SQLGetFunctions(hdbc, SQL_API_ALL_FUNCTIONS, fExists);  
  
/* SQLGetFunctions is completed successfully and SQLTables, SQLColumns, and SQLStatistics are supported by the driver. */  
if (retcode == SQL_SUCCESS &&   
fExists[SQL_API_SQLTABLES] == SQL_TRUE &&  
   fExists[SQL_API_SQLCOLUMNS] == SQL_TRUE &&  
   fExists[SQL_API_SQLSTATISTICS] == SQL_TRUE)   
{  
  
   /* Continue with application */  
  
}  
  
SQLDisconnect(hdbc);  
```  
  
## <a name="related-functions"></a>Funciones relacionadas  
  
|Para obtener información acerca de|Vea|  
|---------------------------|---------|  
|Devolver el valor de un atributo de conexión|[Función SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Devolver información acerca de un controlador o un origen de datos|[Función SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|Devolver el valor de un atributo de instrucción|[Función SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de la API de ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Archivos de encabezado de ODBC](../../../odbc/reference/install/odbc-header-files.md)
