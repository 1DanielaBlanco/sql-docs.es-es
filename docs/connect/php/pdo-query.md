---
title: 'PDO:: Query | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f6f5e6d4-8ca9-4f06-89ed-de65ad3952a2
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c945bb5ab0a14b1c93b0c7f4fb16a72cd258bb14
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "37979749"
---
# <a name="pdoquery"></a>PDO::query
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Ejecuta una consulta SQL y devuelve un conjunto de resultados como un objeto PDOStatement.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
PDOStatement PDO::query ($statement[, $fetch_style);  
```  
  
#### <a name="parameters"></a>Parámetros  
*$statement*: la instrucción SQL que se quiere ejecutar.  
  
*$fetchstyle*: las instrucciones opcionales sobre cómo realizar la consulta. Para obtener información más detallada, consulte la sección Comentarios.El parámetro  $*fetch_style* de PDO::query puede reemplazarse por $*fetch_style* de PDO::fetch.  
  
## <a name="return-value"></a>Valor devuelto  
Si la llamada se realiza correctamente, PDO::query devuelve un objeto PDOStatement. Si se produce un error en la llamada, PDO::query lanza un objeto PDOException o devuelve el valor False, en función de la configuración de PDO::ATTR_ERRMODE.  
  
## <a name="exceptions"></a>Excepciones  
PDOException.  
  
## <a name="remarks"></a>Notas  
Una consulta ejecutada con PDO::query puede ejecutar una instrucción preparada o directa, en función de la configuración de PDO::SQLSRV_ATTR_DIRECT_QUERY. Para obtener más información, vea [Direct Statement Execution and Prepared Statement Execution in the PDO_SQLSRV Driver (Ejecución de la instrucción preparada o directa en el controlador PDO_SQLSRV)](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md).  
  
PDO::SQLSRV_ATTR_QUERY_TIMEOUT también afecta al comportamiento de PDO::exec; vea [PDO::setAttribute](../../connect/php/pdo-setattribute.md).  
  
Puede especificar las siguientes opciones para $*fetch_style*.  
  
|style|Descripción|  
|---------|---------------|  
|PDO::FETCH_COLUMN, *num*|Consultas de datos de la columna especificada. La primera columna de la tabla es 0.|  
|PDO::FETCH_CLASS, "*NombreDeClase*", array( *listaArgumentos* )|Crea una instancia de una clase y asigna nombres de columna a las propiedades de la clase. Si el constructor de clase toma uno o varios parámetros, también se puede transmitir un objeto *arglist*.|  
|PDO:: fetch_class, '*classname*'|Asigna nombres de columna a las propiedades de una clase existente.|  
  
Llame a PDOStatement::closeCursor para liberar recursos de base de datos asociados al objeto PDOStatement antes de volver a llamar a PDO::query.  
  
Puede cerrar un objeto PDOStatement si se establece el valor en Null.  
  
Si no se recuperan todos los datos de un conjunto de resultados, la siguiente llamada a PDO::query se realizará correctamente.  
  
En la versión 2.0 de los [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], se agregó compatibilidad con PDO.  
  
## <a name="example"></a>Ejemplo  
En este ejemplo se muestran varias consultas.  
  
```  
<?php  
$database = "AdventureWorks";  
$conn = new PDO( "sqlsrv:server=(local) ; Database = $database", "", "");  
$conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );  
$conn->setAttribute( PDO::SQLSRV_ATTR_QUERY_TIMEOUT, 1 );  
  
$query = 'select * from Person.ContactType';  
  
// simple query  
$stmt = $conn->query( $query );  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print_r( $row['Name'] ."\n" );  
}  
  
echo "\n........ query for a column ............\n";  
  
// query for one column  
$stmt = $conn->query( $query, PDO::FETCH_COLUMN, 1 );  
while ( $row = $stmt->fetch() ){  
   echo "$row\n";  
}  
  
echo "\n........ query with a new class ............\n";  
$query = 'select * from HumanResources.Department order by GroupName';  
// query with a class  
class cc {  
   function __construct( $arg ) {  
      echo "$arg";  
   }  
  
   function __toString() {  
      return $this->DepartmentID . "; " . $this->Name . "; " . $this->GroupName;  
   }  
}  
  
$stmt = $conn->query( $query, PDO::FETCH_CLASS, 'cc', array( "arg1 " ));  
  
while ( $row = $stmt->fetch() ){  
   echo "$row\n";  
}  
  
echo "\n........ query into an existing class ............\n";  
$c_obj = new cc( '' );  
$stmt = $conn->query( $query, PDO::FETCH_INTO, $c_obj );  
while ( $stmt->fetch() ){  
   echo "$c_obj\n";  
}  
  
$stmt = null;  
?>  
```  
  
## <a name="see-also"></a>Ver también  
[Clase PDO](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
