---
title: 'Pdostatement:: Bindcolumn | Documentos de Microsoft'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: bbdcea53-d23d-4769-89a0-95c7cf4d5390
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b01f19dcb7b55da9c547d07d07784fe1730cdd66
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35308454"
---
# <a name="pdostatementbindcolumn"></a>PDOStatement::bindColumn
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Enlaza una variable a una columna de un juego de resultados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
bool PDOStatement::bindColumn($column, &$param[, $type[, $maxLen[, $driverdata ]]] );  
```  
  
#### <a name="parameters"></a>Parámetros  
$*columna*: el número (mixto) de la columna (índice basado en 1) o el nombre de la columna del conjunto de resultados.  
  
&$*param*: el nombre (mixto) de la variable PHP a la que se enlazará la columna.  
  
$*tipo de*: el tipo de datos opcional del parámetro, representado por una constante PDO:: param_ *.  
  
$*maxLen*: un valor entero opcional que no usan los controladores de Microsoft para PHP para SQL Server.  
  
$*driverdata*: el controlador de parámetros mixtos opcionales. Por ejemplo, podría especificar PDO::SQLSRV_ENCODING_UTF8 para enlazar la columna a una variable como una cadena codificada en UTF-8.  
  
## <a name="return-value"></a>Valor devuelto  
Se devuelve el valor TRUE si la operación se realiza correctamente; de lo contrario, se devuelve FALSE.  
  
## <a name="remarks"></a>Notas  
En la versión 2.0 de los [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], se agregó compatibilidad con PDO.  
  
## <a name="example"></a>Ejemplo  
En este ejemplo se muestra cómo se puede enlazar una variable a una columna de un conjunto de resultados.  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "SELECT Title, FirstName, EmailAddress FROM Person.Contact where LastName = 'Estes'";  
$stmt = $conn->prepare($query);  
$stmt->execute();  
  
$stmt->bindColumn('EmailAddress', $email);  
while ( $row = $stmt->fetch( PDO::FETCH_BOUND ) ){  
   echo "$email\n";  
}  
?>  
```  
  
## <a name="see-also"></a>Vea también  
[Clase PDOStatement](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
