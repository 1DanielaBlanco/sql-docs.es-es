---
title: Quitar base de datos (Transact-SQL) | Documentos de Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 09/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP DATABASE
- DROP_DATABASE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots [SQL Server database snapshots], deleting
- removing databases
- database snapshots [SQL Server], removing
- deleting databases
- dropping databases
- databases [SQL Server], dropping
- DROP DATABASE statement
- database removal [SQL Server], DROP DATABASE statement
ms.assetid: 477396a9-92dc-43c9-9b97-42c8728ede8e
caps.latest.revision: 83
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 6e1a96bb64c8cb6a81311f422d370e36d9489ca4
ms.contentlocale: es-es
ms.lasthandoff: 10/24/2017

---
# <a name="drop-database-transact-sql"></a>DROP DATABASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Quita una o varias bases de datos de usuario o instantáneas de base de datos de una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
-- SQL Server Syntax  
DROP DATABASE [ IF EXISTS ] { database_name | database_snapshot_name } [ ,...n ] [;]  
```  
  
```  
-- Azure SQL Database, Azure SQL Data Warehouse and Parallel Data Warehouse Syntax   
DROP DATABASE database_name [;]  
```  
  
## <a name="arguments"></a>Argumentos  
 *IF EXISTE*  
 **Se aplica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a través de la [versión actual](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Condicionalmente quita la base de datos solo si ya existe.  
  
 *database_name*  
 Especifica el nombre de la base de datos que se va a quitar. Para mostrar una lista de bases de datos, use la [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) vista de catálogo.  
  
 *nombre_base_de_datos_de_instantánea*  
 **Se aplica a**: desde [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] hasta [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Especifica el nombre de la instantánea de base de datos que se va a quitar.  
  
## <a name="general-remarks"></a>Notas generales  
 Una base de datos se puede quitar sea cual sea su estado (sin conexión, solo lectura, sospechosa, etc.). Para mostrar el estado actual de una base de datos, use la **sys.databases** vista de catálogo.  
  
 Una base de datos que se ha quitado solo puede volver a crearse si se restaura una copia de seguridad. No es posible realizar copias de seguridad de instantáneas de la base de datos, por lo que éstas no se pueden restaurar.  
  
 Cuando se quita una base de datos, el [base de datos maestra](../../relational-databases/databases/master-database.md) realizar copias de seguridad.  
  
 Al quitar una base de datos, se elimina la base de datos de una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], así como los archivos de disco físico que usa. Si la base de datos o alguno de sus archivos están sin conexión cuando se quita, no se eliminan los archivos de disco. Estos archivos se pueden eliminar manualmente en el Explorador de Windows. Para quitar una base de datos del servidor actual sin eliminar los archivos del sistema de archivos, use [sp_detach_db](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md).  
  
> [!WARNING]  
>  Quitar una base de datos que tiene FILE_SNAPSHOT copias de seguridad asociadas se realizará correctamente, pero no se eliminarán los archivos de base de datos que tienen asociados instantáneas para evitar que se invalide las copias de seguridad que hace referencia a estos archivos de base de datos. El archivo se truncará, pero no se eliminará físicamente con el fin de mantener las copias de seguridad FILE_SNAPSHOT intacta. Para obtener más información, vea [Copia de seguridad y restauración de SQL Server con el servicio de Almacenamiento de blobs de Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md). **Se aplica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a través de [versión actual](http://go.microsoft.com/fwlink/p/?LinkId=299658).  
  
### [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Cuando se quita una instantánea de base de datos, se elimina la instantánea de base de datos de una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], así como los archivos físicos dispersos del sistema de archivos NTFS que emplea. Para obtener información sobre el uso de archivos dispersos con instantáneas de base de datos, vea [instantáneas de base de datos &#40; SQL Server &#41; ](../../relational-databases/databases/database-snapshots-sql-server.md). Al quitar una instantánea de la base de datos se borra la caché del plan para la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Al borrar la memoria caché de planes, se provoca una nueva compilación de todos los planes de ejecución posteriores y puede ocasionar una disminución repentina y temporal del rendimiento de las consultas. Para cada almacén de caché borrado de la memoria caché de planes, el registro de errores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contendrá el siguiente mensaje informativo: "[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha detectado %d instancias de vaciado del almacén de caché '%s' (parte de la memoria caché de planes) debido a determinadas operaciones de mantenimiento de base de datos o reconfiguración". Este mensaje se registra cada cinco minutos siempre que se vacíe la memoria caché dentro de ese intervalo de tiempo.  
  
## <a name="interoperability"></a>Interoperabilidad  
  
### <a name="sql-server"></a>SQL Server  
 Para quitar una base de datos publicada para la replicación transaccional, o suscrita o publicada para la replicación de mezcla, primero es necesario quitar la replicación de la base de datos. Si se daña una base de datos o no se puede quitar la replicación primero, o ambas cosas, la mayoría de las veces todavía se puede quitar la base de datos utilizando ALTER DATABASE para definirla como sin conexión y, después, quitarla.  
  
 Si la base de datos participa en el trasvase de registros, quite el trasvase de registros antes de quitar la base de datos. Para más información, vea [Acerca del trasvase de registros &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).  
  
  
## <a name="limitations-and-restrictions"></a>Limitaciones y restricciones  
 [Las bases de datos de sistema](../../relational-databases/databases/system-databases.md) no se puede quitar.  
  
 La instrucción DROP DATABASE debe ejecutarse en modo de confirmación automática y no se permite en una transacción explícita o implícita. El modo de confirmación automática es el modo de administración de transacciones predeterminado.  
  
 No se puede quitar una base de datos que se está utilizando actualmente. Es decir, que un usuario la tenga abierta para lectura o escritura. Para quitar usuarios de la base de datos, utilice ALTER DATABASE para establecer la base de datos en SINGLE_USER.  
  
### [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Deben quitarse las instantáneas de una base de datos para poder quitar esa base de datos.  
  
 Quitar una base de datos habilitar para Stretch Database no quita los datos remotos. Si desea eliminar los datos remotos, tendrá que quitarlo manualmente.  
  
### [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
 Debe estar conectado a la base de datos maestra para quitar una base de datos.
  
 La instrucción DROP DATABASE debe ser la única instrucción en un lote SQL y solo puede quitar una base de datos cada vez.
  
### [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]  
 Debe estar conectado a la base de datos maestra para quitar una base de datos.
  
 La instrucción DROP DATABASE debe ser la única instrucción en un lote SQL y solo puede quitar una base de datos cada vez.

## <a name="permissions"></a>Permissions  
  
### [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Requiere la **CONTROL** permiso en la base de datos o **ALTER ANY DATABASE** permiso o la pertenencia a la **db_owner** rol fijo de base de datos.  
  
### [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
 Solo el inicio de sesión principal de nivel de servidor (creado por el proceso de aprovisionamiento) o los miembros de la **dbmanager** rol de base de datos puede quitar una base de datos.  
  
### [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Requiere la **CONTROL** permiso en la base de datos o **ALTER ANY DATABASE** permiso o la pertenencia a la **db_owner** rol fijo de base de datos.  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-dropping-a-single-database"></a>A. Quitar una sola base de datos  
 En el ejemplo siguiente se quita la base de datos `Sales`.  
  
```  
DROP DATABASE Sales;  
```  
  
### <a name="b-dropping-multiple-databases"></a>B. Quitar varias bases de datos  
  
**Se aplica a**: desde [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] hasta [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 En el ejemplo siguiente se quita cada una de las bases de datos enumeradas.  
  
```  
DROP DATABASE Sales, NewSales;  
```  
  
### <a name="c-dropping-a-database-snapshot"></a>C. Quitar una instantánea de la base de datos  
  
**Se aplica a**: desde [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] hasta [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 En el ejemplo siguiente se quita una instantánea de base de datos, denominada `sales_snapshot0600`, sin que afecte a la base de datos de origen.  
  
```  
DROP DATABASE sales_snapshot0600;  
```  
  
## <a name="see-also"></a>Vea también  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE &#40;Transact-SQL de SQL Server&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
  

