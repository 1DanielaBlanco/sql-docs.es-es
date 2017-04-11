---
title: "Agregar y quitar publicadores del Monitor de replicaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Monitor de replicación, agregar y quitar publicadores"
ms.assetid: fa36c4b4-bfa5-494e-92e3-07a02d7332c3
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Agregar y quitar publicadores del Monitor de replicaci&#243;n
  El servidor desde el que inicia el Monitor de replicación se agrega automáticamente al monitor si es un publicador. Se pueden agregar más publicadores mediante el cuadro de diálogo **Agregar publicador** . Una vez agregado un publicador, se muestra en un grupo en el panel izquierdo del monitor. El grupo **Mis publicadores** se incluye de manera predeterminada, pero puede crear grupos nuevos para administrar una o más topologías de replicación. Para obtener información acerca de cómo iniciar el Monitor de replicación, vea [iniciar el Monitor de replicación](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### Para agregar un publicador de SQL Server  
  
1.  Haga clic en el **Monitor de replicación** nodo o en un publicador de grupo en el panel izquierdo y, a continuación, haga clic en **Agregar publicador**.  
  
2.  En el cuadro de diálogo **Agregar publicador** , haga clic en **Agregar**y, a continuación, en **Agregar publicador de SQL Server**.  
  
3.  En el cuadro de diálogo **Conectar al servidor** , escriba el nombre del publicador y seleccione el tipo de autenticación. Si selecciona **Autenticación de SQL Server**, escriba un inicio de sesión y una contraseña. El Monitor de replicación guarda las credenciales que especifique para usarlas cuando se conecte con este servidor en el futuro. La cuenta de Windows o el inicio de sesión de SQL Server especificados han de ser miembros del rol fijo de servidor **sysadmin** o del rol fijo de base de datos **replmonitor** en la base de datos de distribución.  
  
4.  Haga clic en **Conectar**. Si el publicador utiliza un distribuidor remoto, se le pedirá que se conecte con el distribuidor en el cuadro de diálogo **Conectar al servidor** . El Monitor de replicación guarda las credenciales que especifique para usarlas cuando se conecte con este servidor en el futuro. La cuenta de Windows o el inicio de sesión de SQL Server especificados han de ser miembros del rol fijo de servidor **sysadmin** o del rol fijo de base de datos **replmonitor** en la base de datos de distribución.  
  
5.  El nombre del publicador y el distribuidor se muestran en el **iniciar la supervisión de los siguientes publicadores** cuadrícula.  
  
6.  Para especificar opciones de actualización y de conexión para el publicador, seleccione el publicador en la cuadrícula y modifique las opciones como sea necesario. Para obtener más información acerca de las opciones de actualización, vea [Caching, Refresh, and Replication Monitor Performance](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md).  
  
7.  Seleccione el grupo bajo el que se debe mostrar el publicador en el Monitor de replicación. Para crear un nuevo grupo, haga clic en **nuevo grupo**, escriba un nombre de grupo, seleccione el grupo en el **Mostrar estos publicadores en el siguiente grupo** lista.  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### Para agregar un publicador de Oracle  
  
1.  Haga clic en el **Monitor de replicación** nodo o en un publicador de grupo en el panel izquierdo y, a continuación, haga clic en **Agregar publicador**.  
  
2.  En el cuadro de diálogo **Agregar publicador** , haga clic en **Agregar**y, a continuación, en **Agregar publicador de Oracle**.  
  
3.  En el cuadro de diálogo **Conectar al servidor** , escriba el nombre del distribuidor de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] asociado con el publicador de Oracle y seleccione el tipo de autenticación. Si selecciona **Autenticación de SQL Server**, escriba un inicio de sesión y una contraseña. El Monitor de replicación guarda las credenciales que especifique para usarlas cuando se conecte con este servidor en el futuro. La cuenta de Windows o el inicio de sesión de SQL Server especificados han de ser miembros del rol fijo de servidor **sysadmin** o del rol fijo de base de datos **replmonitor** en la base de datos de distribución.  
  
4.  Haga clic en **Conectar**.  
  
5.  El nombre del publicador y el distribuidor se muestran en el **iniciar la supervisión de los siguientes publicadores** cuadrícula.  
  
6.  Para especificar opciones de actualización y de conexión para el publicador, seleccione el publicador en la cuadrícula y modifique las opciones como sea necesario. Para obtener más información acerca de las opciones de actualización, vea [Caching, Refresh, and Replication Monitor Performance](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md).  
  
7.  Seleccione el grupo bajo el que se debe mostrar el publicador en el Monitor de replicación. Para crear un nuevo grupo, haga clic en **nuevo grupo**, escriba un nombre de grupo, seleccione el grupo en el **Mostrar estos publicadores en el siguiente grupo** lista.  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### Para agregar uno o más publicadores que utilizan el mismo distribuidor  
  
1.  Haga clic en el **Monitor de replicación** nodo o en un publicador de grupo en el panel izquierdo y, a continuación, haga clic en **Agregar publicador**.  
  
2.  En el cuadro de diálogo **Agregar publicador** , haga clic en **Agregar**y, a continuación, en **Especificar un distribuidor y agregar sus publicadores**.  
  
3.  En el cuadro de diálogo **Conectar al servidor** , escriba el nombre del distribuidor y seleccione el tipo de autenticación. Si selecciona **Autenticación de SQL Server**, escriba un inicio de sesión y una contraseña. El Monitor de replicación guarda las credenciales que especifique para usarlas cuando se conecte con este servidor en el futuro. La cuenta de Windows o el inicio de sesión de SQL Server especificados han de ser miembros del rol fijo de servidor **sysadmin** o del rol fijo de base de datos **replmonitor** en la base de datos de distribución.  
  
4.  Haga clic en **Conectar**.  
  
5.  El nombre del distribuidor y cada publicador se muestran en el **iniciar la supervisión de los siguientes publicadores** cuadrícula. Si un publicador ya se ha agregado al Monitor de replicación, no aparecerá en la cuadrícula.  
  
6.  Para especificar opciones de actualización y de conexión para el publicador, seleccione el publicador en la cuadrícula y modifique las opciones como sea necesario. Para obtener más información acerca de las opciones de actualización, vea [Caching, Refresh, and Replication Monitor Performance](../../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md).  
  
7.  Seleccione el grupo bajo el que se deben mostrar los publicadores en el Monitor de replicación. Para crear un nuevo grupo, haga clic en **nuevo grupo**, escriba un nombre de grupo, seleccione el grupo en el **Mostrar estos publicadores en el siguiente grupo** lista.  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### Para modificar la configuración del publicador y de los grupos de publicador  
  
1.  Haga clic en un publicador en el panel izquierdo y, a continuación, haga clic en **Configuración del publicador**.  
  
2.  Lleve a cabo los cambios que desee en el cuadro de diálogo **Configuración del publicador** :  
  
    -   Para cambiar las credenciales que el Monitor de replicación utiliza para conectarse al servidor, haga clic en **Conexión del publicador** o en **Conexión del distribuidor**, y especifique las credenciales en el cuadro de diálogo **Conectar al servidor** .  
  
    -   Para mover un publicador de un grupo a otro, seleccione el publicador en el **iniciar la supervisión de los siguientes publicadores** cuadrícula y, a continuación, seleccione el nuevo grupo en el **Mostrar estos publicadores en el siguiente grupo** lista.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### Para quitar un publicador del Monitor de replicación  
  
1.  Haga clic con el botón secundario en un publicador en el panel izquierdo.  
  
2.  Haga clic en **Quitar**.  
  
### Para quitar un grupo de publicador del Monitor de replicación  
  
1.  Los grupos de publicador se pueden crear solamente cuando se agrega un publicador o se modifica la configuración de un publicador. Para obtener más información, vea los temas de procedimientos sobre cómo agregar un publicador.  
  
### Para quitar un grupo de publicador del Monitor de replicación  
  
1.  Mueva todos los publicadores a un grupo diferente o quítelos del Monitor de replicación. Para obtener más información, vea los procedimientos anteriores de este tema.  
  
2.  Haga clic en el grupo de publicador y, a continuación, haga clic en **quitar**.  
  
## Vea también  
 [Configurar la distribución](../../../relational-databases/replication/configure-distribution.md)   
 [Supervisar la replicación](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  