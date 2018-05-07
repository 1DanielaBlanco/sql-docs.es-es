---
title: Resistencia de conexión inactiva
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.suite: sql
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: david-puglielli
ms.author: v-dapugl
manager: v-hakaka
ms.openlocfilehash: b2ffbf3ef57db31fcfd3a714fe9e2f6e0565237f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="idle-connection-resiliency"></a>Resistencia de conexión inactiva
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Resistencia de conexión](https://msdn.microsoft.com/library/dn632678.aspx) es el principio que puede puede restablecer una conexión inactiva interrumpida, dentro de determinadas restricciones. Si se produce un error en una conexión a Microsoft SQL Server, la resistencia de conexión permite al cliente intenta automáticamente restablecer la conexión. Resistencia de conexión es una propiedad del origen de datos; solo SQL Server 2014 y versiones posterior y base de datos de SQL Azure compatible con la resistencia de conexión.

Resistencia de conexión se implementa con dos palabras clave de conexión que se pueden agregar a cadenas de conexión: **ConnectRetryCount** y **ConnectRetryInterval**.

|Palabra clave|Valores|Predeterminado|Description|
|-|-|-|-|
|**ConnectRetryCount**| Número entero comprendido entre 0 y 255 (ambos inclusive)|1|El número máximo de intentos para restablecer una conexión interrumpida antes de desistir. De forma predeterminada, se realiza un intento único para volver a establecer una conexión cuando se divide. Un valor de 0 significa que no se intentará ninguna reconexión.|
|**ConnectRetryInterval**| Número entero comprendido entre 1 y 60 (inclusive)|1| El tiempo, en segundos, entre los intentos para restablecer una conexión. La aplicación intentará volver a conectarse inmediatamente cuando detecta una conexión interrumpida y, a continuación, esperará **ConnectRetryInterval** segundos antes de volver a intentarlo. Esta palabra clave se omite si **ConnectRetryCount** es igual a 0.

Si el producto de **ConnectRetryCount** multiplicado por **ConnectRetryInterval** es mayor que **LoginTimeout**, a continuación, el cliente dejará de intentar conectarse una vez  **LoginTimeout** se alcanza; en caso contrario, continuará intentar volver a conectarse hasta que **ConnectRetryCount** se alcanza.

#### <a name="remarks"></a>Comentarios

Resistencia de conexión se aplica cuando la conexión está inactiva. Errores que se producen al ejecutar una transacción, por ejemplo, no se desencadenarán intentos de reconexión: se producirá un error tal y como se esperaría en caso contrario. Las situaciones siguientes, conocidas como estados de sesión no podrán recuperarse, no desencadenarán intentos de reconexión:

* Tablas temporales
* Cursores globales y locales
* Bloqueos de transacciones de nivel de contexto de transacción y sesión
* Bloqueos de aplicación
* EXECUTE AS / REVERTIR el contexto de seguridad
* Identificadores de automatización OLE
* Identificadores XML preparados
* Marcas de seguimiento

## <a name="example"></a>Ejemplo

El código siguiente se conecta a una base de datos y ejecuta una consulta. La conexión se interrumpe por la terminación de la sesión y se intenta una consulta nueva usando la conexión rota. Este ejemplo se utiliza la [AdventureWorks](https://msdn.microsoft.com/library/ms124501%28v=sql.100%29.aspx) base de datos de ejemplo.

En este ejemplo, especificamos un cursor en búfer antes de interrumpir la conexión. Si no se especifica un cursor en búfer, ¿no puede restablecer la conexión ya que sería un cursor de servidor activo y, por tanto, la conexión no estaría inactiva cuando dañado. Sin embargo, en ese caso se puede llamar a sqlsrv_free_stmt() antes de interrumpir la conexión para que deje vacante el cursor y se puede restablecer correctamente la conexión.

```php
<?php
// This function breaks the connection by determining its session ID and killing it.
// A separate connection is used to break the main connection because a session
// cannot kill itself. The sleep() function ensures enough time has passed for KILL
// to finish ending the session.
function BreakConnection( $conn, $conn_break )
{
    $stmt1 = sqlsrv_query( $conn, "SELECT @@SPID" );
    if ( sqlsrv_fetch( $stmt1 ) )
    {
        $spid=sqlsrv_get_field( $stmt1, 0 );
    }

    $stmt2 = sqlsrv_prepare( $conn_break, "KILL ".$spid );
    sqlsrv_execute( $stmt2 );
    sleep(1);
}

// Connect to the local server using Windows authentication and specify
// AdventureWorks as the database in use. Specify values for
// ConnectRetryCount and ConnectRetryInterval as well.
$databaseName = 'AdventureWorks2014';
$serverName = '(local)';
$connectionInfo = array( "Database"=>$databaseName, "ConnectRetryCount"=>10, "ConnectRetryInterval"=>10 );

$conn = sqlsrv_connect( $serverName, $connectionInfo );
if( $conn === false)  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}

// A separate connection that will be used to break the main connection $conn
$conn_break = sqlsrv_connect( $serverName, array( "Database"=>$databaseName) );

// Create a statement to retrieve the contents of a table
$stmt1 = sqlsrv_query( $conn, "SELECT * FROM HumanResources.Employee",
                       array(), array( "Scrollable"=>"buffered" ) );
if( $stmt1 === false )
{
     echo "Error in statement 1.\n";
     die( print_r( sqlsrv_errors(), true ));
}
else
{
    echo "Statement 1 successful.\n";
    $rowcount = sqlsrv_num_rows( $stmt1 );
    echo $rowcount." rows in result set.\n";
}

// Now break the connection $conn
BreakConnection( $conn, $conn_break );

// Create another statement. The connection will be reestablished.
$stmt2 = sqlsrv_query( $conn, "SELECT * FROM HumanResources.Department",
                       array(), array( "Scrollable"=>"buffered" ) );
if( $stmt2 === false )
{
     echo "Error in statement 2.\n";
     die( print_r( sqlsrv_errors(), true ));
}
else
{
    echo "Statement 2 successful.\n";
    $rowcount = sqlsrv_num_rows( $stmt2 );
    echo $rowcount." rows in result set.\n";
}

sqlsrv_close( $conn );
sqlsrv_close( $conn_break );
?>
```
Resultado esperado:
```
Statement 1 successful.
290 rows in result set.
Statement 2 successful.
16 rows in result set.
```

## <a name="see-also"></a>Vea también
[Resistencia de conexión en el controlador Windows ODBC](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver)
