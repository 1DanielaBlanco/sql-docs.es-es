---
title: "Configurar opciones de inicio del servidor (Administrador de configuraci&#243;n de SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "parámetros [SQL Server], opciones de inicio"
  - "SQL Server, opciones de inicio"
  - "modo de usuario único [SQL Server], iniciar en"
  - "opciones de inicio [SQL Server]"
  - "servicios SQL Server, configurar opciones de inicio"
ms.assetid: 7a94643c-6460-4baf-bb31-0cb99eaf970d
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Configurar opciones de inicio del servidor (Administrador de configuraci&#243;n de SQL Server)
  En este tema se describe cómo configurar las opciones de inicio que se utilizarán cada vez que el [!INCLUDE[ssDE](../../includes/ssde-md.md)] se inicie en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para obtener una lista de opciones de inicio, vea [Opciones de inicio del servicio de motor de base de datos](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
##  <a name="BeforeYouBegin"></a> Antes de empezar  
  
### Limitaciones y restricciones  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] escribe los parámetros de inicio en el Registro. Estos surten efecto en el siguiente inicio de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 En un clúster, se deben efectuar cambios en el servidor activo cuando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] está en línea y surtirán efecto cuando el [!INCLUDE[ssDE](../../includes/ssde-md.md)] se reinicie. La actualización de las opciones de inicio del Registro del otro nodo se producirá tras la siguiente conmutación por error.  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 La configuración de opciones de inicio del servidor está restringida a los usuarios que pueden cambiar las entradas relacionadas del Registro. Esto incluye a los usuarios siguientes.  
  
-   Miembros del grupo local de administradores.  
  
-   La cuenta de dominio utilizada por [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], si el [!INCLUDE[ssDE](../../includes/ssde-md.md)] está configurado para ejecutarse bajo una cuenta de dominio.  
  
##  <a name="SSMSProcedure"></a> Usar el Administrador de configuración de SQL Server  
  
#### Para configurar las opciones de inicio  
  
1.  Haga clic en el botón **Inicio** , seleccione **Todos los programas**, seleccione [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], seleccione **Herramientas de configuración**y, a continuación, haga clic en **Administrador de configuración de SQL Server**.  
  
    > [!NOTE]  
    >  Como el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] es un complemento del programa [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console y no un programa independiente, el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no aparece como aplicación en las versiones más recientes de Windows.  
    >   
    >  -   **Windows 10**:  
    >          Para abrir el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], escriba SQLServerManager13.msc (para [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]) en la **página de inicio**. Para versiones anteriores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , reemplace el 13 por un número inferior. Al hacer clic en SQLServerManager13.msc, se abre el Administrador de configuración. Para anclar el Administrador de configuración a la página de inicio o a la barra de tareas, haga clic con el botón derecho en SQLServerManager13.msc y, después, haga clic en **Abrir ubicación del archivo**. En el Explorador de archivos de Windows, haga clic con el botón derecho en SQLServerManager13.msc y, después, haga clic en **Anclar a Inicio** o **Anclar a la barra de tareas**.  
    > -   **Windows 8**:  
    >          Para abrir el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], escriba **SQLServerManager\<versión>.msc** por ejemplo, **SQLServerManager13.msc**, en el acceso a **Buscar** de **Aplicaciones** y, después, pulse **Entrar**.  
  
2.  En el Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , haga clic en **Servicios de SQL Server**.  
  
3.  En el panel derecho, haga clic con el botón derecho en **SQL Server (***<nombre_instancia>***)** y, luego, haga clic en **Propiedades**.  
  
4.  En la pestaña **Parámetros de inicio** , en el cuadro **Especifique un parámetro de inicio** , escriba el parámetro y, a continuación, haga clic en **Agregar**.  
  
     Por ejemplo, para iniciarlo en modo de usuario único, escriba **-m** en el cuadro **Especifique un parámetro de inicio** y, después, haga clic en **Agregar**. (Al reiniciar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en modo de usuario único, detenga el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. De lo contrario, el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] podría conectarse primero e impedir que se conecte como un segundo usuario).  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  Reinicie el [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
    > [!WARNING]  
    >  Cuando haya terminado de usar el modo de usuario único, en el cuadro Parámetros de inicio, seleccione el parámetro **-m** en el cuadro **Parámetros existentes** y, después, haga clic en **Quitar**. Reinicie el [!INCLUDE[ssDE](../../includes/ssde-md.md)] para restaurar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al modo típico multiusuario.  
  
## Vea también  
 [Iniciar SQL Server en modo de usuario único](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)   
 [Conectarse a SQL Server cuando los administradores del sistema no tienen acceso](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md)   
 [Iniciar, detener o pausar el servicio del Agente SQL Server](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  