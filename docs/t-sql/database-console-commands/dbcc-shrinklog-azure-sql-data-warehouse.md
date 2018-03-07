---
title: DBCC SHRINKLOG (almacenamiento de datos SQL Azure) | Documentos de Microsoft
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d06917a784e507ab5568e28b4d34273f5fe71063
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-shrinklog-azure-sql-data-warehouse"></a>DBCC SHRINKLOG (almacenamiento de datos SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Reduce el tamaño del registro de transacciones *en el dispositivo* actuales [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] base de datos. Los datos se desfragmentan con el fin de reducir el registro de transacciones. Con el tiempo, el registro de transacciones de base de datos puede ser ineficaz y fragmentado. Use DBCC SHRINKLOG para reducir la fragmentación y el tamaño del registro.
  
![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "icono de vínculo de tema") [convenciones de sintaxis de Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintaxis  
  
```sql
DBCC SHRINKLOG   
    [ ( SIZE = { target_size [ MB | GB | TB ]  } | DEFAULT ) ]   
    [ WITH NO_INFOMSGS ]   
[;]  
```  
  
## <a name="arguments"></a>Argumentos  
TAMAÑO = { *target_size* [MB | **GB** | TB]} | **Predeterminado**.  
*target_size* tenga el tamaño deseado para el registro de transacciones, entre todos los nodos de proceso, una vez finalizada DBCC SHRINKLOG. Es un entero mayor que 0.  
El tamaño del registro se mide en megabytes (MB), gigabytes (GB) o terabytes (TB). Es el tamaño combinado del registro de transacciones en todos los nodos de proceso.  
De forma predeterminada, DBCC SHRINKLOG reduce el registro de transacciones para el tamaño de registro almacenado en los metadatos de la base de datos. El tamaño del registro en los metadatos se determina por el parámetro LOG_SIZE en [CREATE DATABASE &#40; Almacenamiento de datos SQL de Azure &#41; ](../../t-sql/statements/create-database-azure-sql-data-warehouse.md) o [ALTER DATABASE &#40; Almacenamiento de datos SQL de Azure &#41; ](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md). DBCC SHRINKLOG reduce el tamaño de registro de transacciones con el valor predeterminado de tamaño cuando `SIZE=DEFAULT` se especifica, o cuando el `SIZE` se omite la cláusula.
  
WITH NO_INFOMSGS  
Mensajes informativos no se muestran en los resultados de DBCC SHRINKLOG.  
  
## <a name="permissions"></a>Permissions  
Requiere el permiso ALTER SERVER STATE.
  
## <a name="general-remarks"></a>Notas generales  
DBCC SHRINKLOG no cambia el tamaño de registro almacenado en los metadatos de la base de datos. Los metadatos continuarán contener el parámetro LOG_SIZE que se especificó en la instrucción CREATE DATABASE o ALTER DATABASE.
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Ejemplos: [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] y[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-shrink-the-transaction-log-to-the-original-size-specified-by-create-database"></a>A. Reducir el registro de transacciones al tamaño original especificado al crear la base de datos.  
Imagine que el registro de transacciones de la base de datos de direcciones se establece en 100 MB cuando se creó la base de datos de direcciones. Es decir, la instrucción CREATE DATABASE para direcciones tenía LOG_SIZE = 100 MB. Ahora, suponga que el registro ha crecido hasta 150 MB y desea reducir a 100 MB.
  
Cada una de las siguientes instrucciones intentará reducir el registro de transacciones para la base de datos de direcciones para el tamaño predeterminado de 100 MB. Si va a reducir el registro a 100 MB producir pérdida de datos, DBCC SHRINKLOG se reducirá el registro a las posibles de tamaño más pequeña, más de 100 MB, sin perder los datos.
  
```sql
USE Addresses;  
DBCC SHRINKLOG ( SIZE = 100 MB );  
DBCC SHRINKLOG ( SIZE = DEFAULT );  
DBCC SHRINKLOG;  
```  
  
  
