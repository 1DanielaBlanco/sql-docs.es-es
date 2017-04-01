---
title: "Ver las propiedades y el contenido de un dispositivo l&#243;gico de copia de seguridad (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mostrar contenido de copia de seguridad"
  - "ver contenido de copia de seguridad"
  - "copias de seguridad de base de datos [SQL Server], ver contenido"
  - "hacer copias de seguridad de bases de datos [SQL Server], ver contenido"
  - "hacer copia de seguridad de bases de datos [SQL Server], propiedades"
  - "mostrar las propiedades de la copia de seguridad"
  - "dispositivos de copia de seguridad [SQL Server], ver información"
  - "ver las propiedades de la copia de seguridad"
  - "copias de seguridad [SQL Server], propiedades"
ms.assetid: 3a309074-e816-454d-b6c3-fcfdde0cbf74
caps.latest.revision: 22
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 22
---
# Ver las propiedades y el contenido de un dispositivo l&#243;gico de copia de seguridad (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  En este tema se describe cómo ver las propiedades y el contenido de un dispositivo lógico de copia de seguridad de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Seguridad](#Security)  
  
-   **Para ver las propiedades y el contenido de un dispositivo lógico de copia de seguridad, utilizando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Security"></a> Seguridad  
 Para obtener información sobre seguridad, vea [RESTORE LABELONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20LABELONLY%20\(Transact-SQL\).md).  
  
####  <a name="Permissions"></a> Permisos  
 En [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] y versiones posteriores, la obtención de información sobre un conjunto de copia de seguridad o un dispositivo de copia de seguridad requiere el permiso CREATE DATABASE. Para obtener más información, vea [GRANT &#40;permisos de base de datos de Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md).  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
  
#### Para ver las propiedades y el contenido de un dispositivo lógico de copia de seguridad  
  
1.  Tras conectarse a la instancia apropiada de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], en el Explorador de objetos, haga clic en el nombre del servidor para expandir el árbol correspondiente.  
  
2.  Expanda **Objetos de servidor**y expanda **Dispositivos de copia de seguridad**.  
  
3.  Haga clic en el dispositivo y, luego, con el botón derecho, haga clic en **Propiedades** para abrir el cuadro de diálogo **Dispositivo de copia de seguridad**.  
  
4.  En la página **General** se muestra el nombre del dispositivo y el destino, que puede ser un dispositivo de cinta o la ruta de acceso de un archivo.  
  
5.  En el panel **Seleccionar una página** , haga clic en **Contenido de los medios**.  
  
6.  El panel de la derecha se muestra en los siguientes paneles de propiedades:  
  
    -   **Multimedia**  
  
         Información de secuencia del medio (número de secuencia del medio, número de secuencia de la familia e identificador del reflejo, si está presente) y la fecha y hora de creación del medio.  
  
    -   **Conjunto de medios**  
  
         Información del conjunto de medios: nombre del conjunto de medios y su descripción, si está disponible, y el número de familias dentro del conjunto de medios.  
  
7.  La cuadrícula **Conjuntos de copia de seguridad** muestra información sobre el contenido del conjunto de medios.  
  
> [!NOTE]  
>  Para obtener más información, vea [Media Contents Page (Página Contenido de los medios)](../../relational-databases/backup-restore/backup-device-media-contents-page.md).  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
  
#### Para ver las propiedades y el contenido de un dispositivo lógico de copia de seguridad  
  
1.  Conéctese con el [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Use la instrucción [RESTORE LABELONLY](../Topic/RESTORE%20LABELONLY%20\(Transact-SQL\).md) . En este ejemplo se devuelve información acerca del dispositivo lógico de copia de seguridad `AdvWrks2008R2Backup`.  
  
```tsql  
USE AdventureWorks2012 ;  
RESTORE LABELONLY  
   FROM AdvWrks2008R2Backup ;  
GO  
  
```  
  
## Vea también  
 [backupfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupmediafamily &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [Dispositivos de copia de seguridad &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)  
  
  