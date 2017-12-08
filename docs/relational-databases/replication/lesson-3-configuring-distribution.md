---
title: "Lección 3: Configuración de la distribución | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
helpviewer_keywords: replication [SQL Server], tutorials
ms.assetid: f248984a-0b59-4c2f-a56d-31f8dafe72b5
caps.latest.revision: "21"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: e7941463e0d36954a0a137be9f003845d9eff1dc
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="lesson-3-configuring-distribution"></a>Lección 3: Configurar la distribución
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] En esta lección configurará la distribución en el publicador y establecerá los permisos requeridos en las bases de datos de publicación y distribución. Si ya ha configurado el distribuidor, debe deshabilitar la publicación y distribución antes de iniciar esta lección. No lo haga si debe mantener una topología de replicación existente.  
  
En este tutorial no se contempla la configuración de un publicador con un distribuidor remoto.  
  
### <a name="configuring-distribution-at-the-publisher"></a>Configurar la distribución en el publicador  
  
1.  Conéctese al publicador en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]y luego expanda el nodo del servidor.  
  
2.  Haga clic con el botón derecho en la carpeta **Replicación** y luego haga clic en **Configurar distribución**.  
  
    > [!NOTE]  
    > Si se ha conectado con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizando **localhost** en lugar del nombre real del servidor, aparecerá una advertencia indicando que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no se puede conectar con el servidor **'localhost'**. En el cuadro de diálogo de advertencia, haga clic en **Aceptar** . En el cuadro de diálogo **Conectar al servidor** , cambie el **Nombre del servidor** de **localhost** al nombre del servidor. Haga clic en **Conectar**.  
  
    Se iniciará el Asistente para configurar la distribución.  
  
3.  En la página **Distribuidor**, seleccione 'nombreDeServidor' actuará como su propio distribuidor; SQL Server creará una base de datos y un registro de distribución** y, luego, haga clic en **Siguiente**.  
  
4.  Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] no se está ejecutando, en la página [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**Inicio del Agente** , seleccione **Sí**, configurar el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servicio del Agente para que se inicie automáticamente. Haga clic en **Siguiente**.  
  
5.  Introduzca **\\\\**\<*nombreDeEquipo>***\repldata** en el cuadro de texto **Carpeta de instantáneas**, donde\<*nombreDeEquipo>* es el nombre del publicador y luego haga clic en **Siguiente**.  
  
6.  Acepte los valores predeterminados en las páginas restantes del asistente.  
  
7.  Haga clic en **Finalizar** para habilitar la distribución.  
  
### <a name="setting-database-permissions-at-the-publisher"></a>Establecer permisos de base de datos en el publicador  
  
1.  En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expanda **Seguridad**, haga clic con el botón derecho en **Inicios de sesión**y, después, seleccione **Nuevo inicio de sesión**.  
  
2.  En la página **General**, haga clic en **Buscar**, escriba \<*nombreDeEquipo>***\repl_snapshot** en el cuadro **Escriba el nombre del objeto que desea seleccionar**, donde \<*nombreDeEquipo>* es el nombre del servidor local del publicador, haga clic en **Comprobar nombres** y, después, haga clic en **Aceptar**.  
  
3.  En la página **Asignación de usuarios** , en la lista **Usuarios asignados a este inicio de sesión** , seleccione las bases de datos de **distribución** y de [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
    En la lista **Pertenencia al rol de la base de datos** , seleccione el rol **db_owner** para el inicio de sesión en ambas bases de datos.  
  
4.  Haga clic en **Aceptar** para crear el inicio de sesión.  
  
5.  Repita los pasos 1 a 4 para crear un inicio de sesión para la cuenta local de repl_logreader. El inicio de sesión también se debe asignar a usuarios que son miembros del rol fijo de base de datos **db_owner** en las bases de datos **distribution** y **AdventureWorks** .  
  
6.  Repita los pasos 1 a 4 para crear un inicio de sesión para la cuenta local de repl_distribution. El inicio de sesión se debe asignar a los usuarios que son miembros del rol fijo de base de datos **db_owner** en la base de datos **distribution** .  
  
7.  Repita los pasos 1 a 4 para crear un inicio de sesión para la cuenta local de repl_merge. Este inicio de sesión debe contar con asignaciones de usuario en las bases de datos **distribution** y **AdventureWorks** .  
  
## <a name="see-also"></a>Vea también  
[Configurar distribución](../../relational-databases/replication/configure-distribution.md)  
[Modelo de seguridad del Agente de replicación](../../relational-databases/replication/security/replication-agent-security-model.md)  
  
  
  
