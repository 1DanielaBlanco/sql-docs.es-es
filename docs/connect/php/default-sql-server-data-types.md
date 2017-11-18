---
title: Valor predeterminado de tipos de datos SQL Server | Documentos de Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- default data types
- converting data types
ms.assetid: 65c7c211-96d3-4e65-a1de-1fe8d21348e7
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b71a28f48cdbfe9e70079abfc392f53976c90c87
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="default-sql-server-data-types"></a>Tipos de datos de SQL Server predeterminados
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Al enviar datos al servidor, los [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] convierten los datos de su tipo de datos PHP a un tipo de datos de SQL Server si el usuario no ha especificado ningún tipo de datos de SQL Server. En la siguiente tabla se muestra el tipo de datos PHP (el tipo de datos que se envían al servidor) y el tipo de datos de SQL Server predeterminado (el tipo de datos al que se convierten los datos). Para obtener información más detallada sobre cómo especificar tipos de datos al enviar datos al servidor, vea [Cómo especificar tipos de datos de SQL Server cuando se usa el controlador SQLSRV](../../connect/php/how-to-specify-sql-server-data-types-when-using-the-sqlsrv-driver.md).  
  
|Tipo de datos PHP|Tipo de datos de SQL Server predeterminados en el controlador SQLSRV|Tipo de datos de SQL Server predeterminados en el controlador PDO_SQLSRV Driver|  
|-----------------|------------------------------------------------|-----------------------------------------------------|  
|NULL|varchar(1)|No compatible|  
|Boolean|bit|bit|  
|Integer|int|int|  
|Float|float(24)|No compatible|  
|String (longitud inferior a 8000 bytes)|varchar (<string length>)|varchar (<string length>)|  
|String (longitud superior a 8000 bytes)|varchar(max)|varchar(max)|  
|Recurso|No compatible.|No compatible.|  
|Stream (codificación: no binaria)|varchar(max)|varchar(max)|  
|Stream (codificación: binaria)|varbinary|varbinary|  
|Array|No compatible.|No compatible.|  
|Object|No compatible.|No compatible.|  
|DateTime (1)|datetime|No compatible.|  
  
## <a name="see-also"></a>Vea también  
[Constantes &#40;controladores de Microsoft para PHP para SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
[Converting Data Types](../../connect/php/converting-data-types.md)  
[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)  
[Tipos de datos PHP](http://go.microsoft.com/fwlink/?LinkId=109071)  
[Tipos de datos (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=109068)  
  

