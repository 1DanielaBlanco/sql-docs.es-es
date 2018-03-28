---
title: PDOStatement::bindParam | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65212058-2632-47a4-ba7d-2206883abf09
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0d4dea9ea34f0a2b41db42f641b89ea074139643
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2018
---
# <a name="pdostatementbindparam"></a>PDOStatement::bindParam
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Enlaza un parámetro a un marcador de posición con nombre o signo de interrogación en la instrucción SQL.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
bool PDOStatement::bindParam($parameter, &$variable[, $data_type[, $length[, $driver_options]]]);  
```  
  
#### <a name="parameters"></a>Parámetros  
$*parámetro*: un identificador de parámetro (mixto). En una instrucción que usa marcadores de posición, utilice un nombre de parámetro (: nombre). Para una instrucción preparada mediante la sintaxis de signo de interrogación, es el índice basado en 1 del parámetro.  
  
&$*variable*: el nombre (mixto) de la variable PHP para enlazar con el parámetro de instrucción SQL.  
  
$*data_type*: An optional (integer) PDO::PARAM_* constant. Valor predeterminado es PDO:: param_str.  
  
$*longitud*: una longitud opcional (valor entero) del tipo de datos. Puede especificar PDO:: sqlsrv_param_out_default_size para indicar el tamaño predeterminado al usar PDO:: param_int o PDO:: param_bool en $*data_type*.  
  
$*driver_options*: las opciones específicas del controlador (mixtas) opcionales. Por ejemplo, podría especificar PDO::SQLSRV_ENCODING_UTF8 para enlazar la columna a una variable como una cadena codificada en UTF-8.  
  
## <a name="return-value"></a>Valor devuelto  
Se devuelve True si la operación se realiza correctamente; de lo contrario, False.  
  
## <a name="remarks"></a>Comentarios  
Cuando se enlazan datos null para las columnas de tipo varbinary, binary o varbinary (max) de servidor debe especificar la codificación binaria (PDO:: sqlsrv_encoding_binary) con $*driver_options*. Para obtener más información acerca de las constantes de codificación, vea [constantes](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md).  
  
En la versión 2.0 de los [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], se agregó compatibilidad con PDO.  

## <a name="example"></a>Ejemplo  
En este ejemplo de código se muestra que después de que $contact se enlace al parámetro, al cambiar el valor, se modifica el valor transmitido en la consulta.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->bindParam(1, $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
  
$stmt = null;  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = :contact");  
$stmt->bindParam(':contact', $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
?>  
```  
  
## <a name="example"></a>Ejemplo  
En este ejemplo de código se muestra cómo obtener acceso a un parámetro de salida.  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$input1 = 'bb';  
  
$stmt = $conn->prepare("select ? = count(*) from Sys.tables");  
$stmt->bindParam(1, $input1, PDO::PARAM_STR, 10);  
$stmt->execute();  
echo $input1;  
?>  
```  
  
## <a name="example"></a>Ejemplo  
En este ejemplo de código se muestra cómo utilizar un parámetro de entrada/salida.  
  
```  
<?php  
   $database = "AdventureWorks";  
   $server = "(local)";  
   $dbh = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
   $dbh->query("IF OBJECT_ID('dbo.sp_ReverseString', 'P') IS NOT NULL DROP PROCEDURE dbo.sp_ReverseString");  
   $dbh->query("CREATE PROCEDURE dbo.sp_ReverseString @String as VARCHAR(2048) OUTPUT as SELECT @String = REVERSE(@String)");  
   $stmt = $dbh->prepare("EXEC dbo.sp_ReverseString ?");  
   $string = "123456789";  
   $stmt->bindParam(1, $string, PDO::PARAM_STR | PDO::PARAM_INPUT_OUTPUT, 2048);  
   $stmt->execute();  
   print $string;   // Expect 987654321  
?>  
```  

> [!NOTE]
> Se recomienda usar cadenas como entradas al enlazar los valores para un [columna decimal o numeric](https://docs.microsoft.com/en-us/sql/t-sql/data-types/decimal-and-numeric-transact-sql) para garantizar la precisión y la exactitud PHP limitó precisión para [números de punto flotante](http://php.net/manual/en/language.types.float.php).

## <a name="example"></a>Ejemplo  
Este ejemplo de código muestra cómo enlazar un valor decimal como un parámetro de entrada.  

```
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  

// Assume TestTable exists with a decimal field 
$input = 9223372036854.80000;
$stmt = $conn->prepare("INSERT INTO TestTable (DecimalCol) VALUES (?)");
// by default it is PDO::PARAM_STR, rounding of a large input value may
// occur if PDO::PARAM_INT is specified
$stmt->bindParam(1, $input, PDO::PARAM_STR);
$stmt->execute();
```


## <a name="see-also"></a>Vea también  
[Clase PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
