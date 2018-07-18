---
title: Creación de un inicio de sesión | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: t-sql
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
helpviewer_keywords:
- creating a login
ms.assetid: a2512310-bdb6-41dc-858a-e866b2b58afc
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 75c029fef31b5406920dd9998460648e9df1ea57
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37429114"
---
# <a name="lesson-2-1---creating-a-login"></a>Lección 2-1: Creación de un inicio de sesión
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]
Para tener acceso a [!INCLUDE[ssDE](../includes/ssde-md.md)], los usuarios necesitan un inicio de sesión. El inicio de sesión puede representar la identidad del usuario como una cuenta de Windows o como un miembro de un grupo de Windows, o el inicio de sesión puede ser un inicio de sesión de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] que solo exista en [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Siempre que sea posible, use la autenticación de Windows.  
  
De forma predeterminada, los administradores del equipo tienen acceso total a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Para esta lección, deseamos tener un usuario con menos privilegios; por tanto, creará una nueva cuenta de autenticación de Windows local en el equipo. Para hacerlo, debe ser un administrador del equipo. A continuación, concederá al nuevo usuario acceso a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
### <a name="to-create-a-new-windows-account"></a>Para crear una cuenta de Windows nueva  
  
1.  Haga clic en **Inicio**y en **Ejecutar**, en el cuadro **Abrir** , escriba **%SystemRoot%\system32\compmgmt.msc /s**y, después, haga clic en **Aceptar** para abrir el programa Administración de equipos.  
  
2.  En **Herramientas del sistema**, expanda **Usuarios y grupos locales**, haga clic con el botón derecho en **Usuarios**y luego haga clic en **Nuevo usuario**.  
  
3.  En el cuadro **Nombre de usuario** , escriba **Mary**.  
  
4.  En los cuadros **Contraseña** y **Confirmar contraseña** , escriba una contraseña segura y, a continuación, haga clic en **Crear** para crear un nuevo usuario de Windows local.  
  
### <a name="to-create-a-login"></a>Para crear un inicio de sesión  
  
1.  En una ventana del Editor de consultas de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], escriba y ejecute el siguiente código reemplazando `computer_name` con el nombre del equipo. `FROM WINDOWS` indica que Windows autenticará al usuario. El argumento opcional `DEFAULT_DATABASE` conecta `Mary` con la base de datos `TestData` , a menos que la cadena de conexión indique otra base de datos. Esta instrucción introduce el punto y coma como una terminación opcional de una instrucción [!INCLUDE[tsql](../includes/tsql-md.md)] .  
  
    ```  
    CREATE LOGIN [computer_name\Mary]  
        FROM WINDOWS  
        WITH DEFAULT_DATABASE = [TestData];  
    GO  
    ```  
  
    Esto autoriza al nombre de usuario `Mary`, autenticado por el equipo, a tener acceso a esta instancia de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Si existe más de una instancia de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] en el equipo, debe crear el inicio de sesión en cada instancia a la que `Mary` deba tener acceso.  
  
    > [!NOTE]  
    > Puesto que `Mary` no es una cuenta de dominio, este nombre de usuario solo puede autenticarse en este equipo.  
  
## <a name="next-task-in-lesson"></a>Siguiente tarea de la lección  
[Conceder acceso a una base de datos](../t-sql/lesson-2-2-granting-access-to-a-database.md)  
  
## <a name="see-also"></a>Ver también  
[CREATE LOGIN &#40;Transact-SQL&#41;](../t-sql/statements/create-login-transact-sql.md)  
[Elegir un modo de autenticación](../relational-databases/security/choose-an-authentication-mode.md)  
  
  
  
