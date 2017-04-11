---
title: "Configurar la opci&#243;n de configuraci&#243;n del servidor Acceso remoto | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servidores remotos [SQL Server], ejecución de procedimiento almacenado"
ms.assetid: f5de748d-1c55-4714-9661-38fe62e5095f
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# Configurar la opci&#243;n de configuraci&#243;n del servidor Acceso remoto
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  En este tema se abarca la característica "Acceso remoto". Se trata de una característica de comunicación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] poco clara que está en desuso y que probablemente no debería usar. Si llegó a esta página porque tiene problemas para conectarse a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consulte uno de los siguientes temas:  
  
-   [Tutorial: Introducción al motor de base de datos](../../relational-databases/tutorial-getting-started-with-the-database-engine.md)  
  
-   [Iniciar una sesión en SQL Server](../../database-engine/configure-windows/logging-in-to-sql-server.md)  
  
-   [Conectarse a SQL Server cuando los administradores del sistema no tienen acceso](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md)  
  
-   [Conectarse a un servidor registrado &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/connect-to-a-registered-server-sql-server-management-studio.md)  
  
-   [Conectar a un componente de SQL Server desde SQL Server Management Studio](../../ssms/f1-help/connect-to-any-sql-server-component-from-sql-server-management-studio.md)  
  
-   [Conectarse al motor de base de datos con sqlcmd](../../relational-databases/scripting/connect-to-the-database-engine-with-sqlcmd.md)  
  
-   [Cómo solucionar problemas de conexión al motor de base de datos de SQL Server](http://social.technet.microsoft.com/wiki/contents/articles/2102.how-to-troubleshoot-connecting-to-the-sql-server-database-engine.aspx)  
  
 Puede que a los programadores les interesen los temas siguientes:  
  
-   [Conectar con SQL Server mediante Autenticación de SQL en ASP.NET 2.0](https://msdn.microsoft.com/library/ff648340.aspx)  
  
-   [Conectarse a una instancia de SQL Server](https://msdn.microsoft.com/library/ms162132.aspx)  
  
-   [Crear conexiones a Bases de datos de SQL Server](https://msdn.microsoft.com/library/s4yys16a.aspx)  
  
 **Aquí comienza el cuerpo principal de este tema.**  
  
 En este tema se describe cómo establecer la opción de configuración del servidor **acceso remoto** en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. La opción **acceso remoto** controla la ejecución de los procedimientos almacenados desde servidores remotos o locales en los que se están ejecutando instancias de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . El valor predeterminado para esta opción es 1. Este valor concede el permiso para ejecutar los procedimientos almacenados locales desde servidores remotos o los procedimientos almacenados remotos desde el servidor local. Para evitar que los procedimientos almacenados locales se ejecuten desde un servidor remoto o que los procedimientos almacenados remotos se ejecuten desde un servidor local, establezca la opción en 0.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Use en su lugar [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) .  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Limitaciones y restricciones](#Restrictions)  
  
     [Seguridad](#Security)  
  
-   **Para configurar la opción de acceso remoto, use:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Seguimiento:**  [Después de configurar la opción de acceso remoto](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Restrictions"></a> Limitaciones y restricciones  
  
-   La opción de **acceso remoto** solo se aplica a los servidores agregados mediante [sp_addserver](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)y se incluye por compatibilidad con versiones anteriores.  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 De forma predeterminada, todos los usuarios tienen permisos de ejecución en **sp_configure** sin ningún parámetro o solo con el primero. Para ejecutar **sp_configure** con ambos parámetros y cambiar una opción de configuración, o para ejecutar la instrucción RECONFIGURE, un usuario debe tener el permiso ALTER SETTINGS en el nivel de servidor. Los roles fijos de servidor **sysadmin** y **serveradmin** tienen el permiso ALTER SETTINGS de forma implícita.  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
  
#### Para configurar la opción de acceso remoto  
  
1.  En el Explorador de objetos, haga clic con el botón derecho en un servidor y seleccione **Propiedades**.  
  
2.  Haga clic en el nodo **Conexiones** .  
  
3.  En **Conexiones a servidores remotos**, active o desactive la casilla **Permitir conexiones remotas con este servidor** .  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
  
#### Para configurar la opción de acceso remoto  
  
1.  Conéctese con el [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**. En este ejemplo se muestra cómo usar [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) para establecer el valor de la opción de `remote access` en `0`.  
  
```tsql  
EXEC sp_configure 'remote access', 0 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 Para obtener más información, vea [Server Configuration Options &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Seguimiento: Después de configurar la opción de acceso remoto  
 Esta configuración no surte efecto hasta que reinicie SQL Server.  
  
## Vea también  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Opciones de configuración de servidor &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  