---
title: "Restaurar la base de datos maestra (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "base de datos maestra [SQL Server], restaurar"
ms.assetid: c83d802c-e84e-4458-b3ca-173d9ba32f73
caps.latest.revision: 42
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 42
---
# Restaurar la base de datos maestra (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  En este tema se explica cómo restaurar la base de datos **maestra** desde una copia de seguridad de base de datos completa.  
  
### Para restaurar la base de datos maestra  
  
1.  Inicie la instancia de servidor en modo de usuario único.  
  
     Para obtener más información sobre cómo especificar el parámetro de inicio de usuario único (**-m**), vea [Configurar opciones de inicio del servidor &#40;Administrador de configuración de SQL Server&#41;](../../database-engine/configure-windows/configure-server-startup-options-sql-server-configuration-manager.md).  
  
2.  Para restaurar una copia de seguridad de base de datos completa de **maestra**, use la siguiente instrucción [RESTORE DATABASE](../Topic/RESTORE%20\(Transact-SQL\).md)[!INCLUDE[tsql](../../includes/tsql-md.md)] :  
  
     `RESTORE DATABASE master FROM`  *<dispositivo_de_copia_de_seguridad>*  `WITH REPLACE`  
  
     La opción REPLACE indica a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que restaure la base de datos especificada incluso cuando ya exista otra con el mismo nombre. La base de datos existente, si existe, se elimina. En el modo de usuario único, es recomendable introducir la instrucción RESTORE DATABASE en la [utilidad sqlcmd](../../tools/sqlcmd-utility.md). Para obtener más información, vea [Usar la utilidad sqlcmd](../../relational-databases/scripting/use-the-sqlcmd-utility.md).  
  
    > [!IMPORTANT]  
    >  Después de que la base de datos **maestra** se haya restaurado, la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se cierra y finaliza el proceso **sqlcmd** . Antes de reiniciar la instancia de servidor, quite el parámetro de inicio de usuario único. Para obtener más información, vea [Configurar opciones de inicio del servidor &#40;Administrador de configuración de SQL Server&#41;](../../database-engine/configure-windows/configure-server-startup-options-sql-server-configuration-manager.md).  
  
3.  Reinicie la instancia del servidor y continúe con otros pasos de la recuperación, por ejemplo, restaurando otras bases de datos, adjuntando bases de datos y corrigiendo incoherencias de los usuarios.  
  
## Ejemplo  
 El ejemplo siguiente restaura la base de datos `master` en la instancia de servidor predeterminada. En el ejemplo se asume que la instancia de servidor ya se ejecuta en modo de usuario único. El ejemplo inicia `sqlcmd` y ejecuta una instrucción `RESTORE DATABASE` que restaura una copia de seguridad de base de datos completa de `master` desde un dispositivo de disco: `Z:\SQLServerBackups\master.bak`.  
  
> [!NOTE]  
>  Para una instancia con nombre, el comando **sqlcmd** debe especificar la opción **-S***\<nombreDeEquipo>*\\*\<nombreDeInstancia>*.  
  
```  
  
      C:\> sqlcmd  
1> RESTORE DATABASE master FROM DISK = 'Z:\SQLServerBackups\master.bak' WITH REPLACE;  
2> GO  
```  
  
## Vea también  
 [Restauraciones de base de datos completas &#40;modelo de recuperación simple&#41;](../../relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md)   
 [Restauraciones de base de datos completas &#40;modelo de recuperación completa&#41;](../../relational-databases/backup-restore/complete-database-restores-full-recovery-model.md)   
 [Solucionar problemas de usuarios huérfanos &#40;SQL Server&#41;](../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md)   
 [Adjuntar y separar bases de datos &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [Volver a generar bases de datos del sistema](../../relational-databases/databases/rebuild-system-databases.md)   
 [Opciones de inicio del servicio de motor de base de datos](../../database-engine/configure-windows/database-engine-service-startup-options.md)   
 [Administrador de configuración de SQL Server](../../relational-databases/sql-server-configuration-manager.md)   
 [Realizar copias de seguridad y restaurar bases de datos del sistema &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)   
 [Iniciar SQL Server en modo de usuario único](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)  
  
  