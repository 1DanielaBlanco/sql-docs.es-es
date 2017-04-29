---
title: "Conectarse al servidor (página Propiedades de conexión del motor de base de datos) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.connecttoce.connectionproperties.f1
- sql13.swb.connecttosqlserver.connectionproperties.f1
ms.assetid: edc1143c-6a47-4b02-92ab-441bdea8ea8a
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 22cef3465036947ad6389b41c4c80bfc5ef965cb
ms.lasthandoff: 04/11/2017

---
# <a name="connect-to-server-connection-properties-page-database-engine"></a>Conectar al servidor (página Propiedades de conexión del motor de base de datos)
Use esta pestaña para ver o especificar opciones cuando se conecte a una instancia de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)] o cuando registre [!INCLUDE[ssDE](../../includes/ssde_md.md)] en **Servidores registrados**. **Conectar** y **Opciones** solo aparecen en este cuadro de diálogo al conectarse a una instancia del [!INCLUDE[ssDE](../../includes/ssde_md.md)]. **Probar** y **Guardar** solo aparecen en este cuadro de diálogo al registrar [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
## <a name="options"></a>Opciones  
**Conectar con base de datos**  
Seleccione en la lista una base de datos a la que conectarse. Si selecciona **<default>**, se conectará a la base de datos predeterminada del servidor. Si selecciona **<Browse server>**, podrá buscar el servidor de la base de datos a la que se conecta.  
  
Al conectarse a una instancia del motor de base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] a través de la base de datos de [!INCLUDE[ssSDSfull](../../includes/sssdsfull_md.md)], es preciso que use la autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] y especifique una base de datos en el cuadro de diálogo **Conectar al servidor** en la pestaña **Propiedades de conexión** . Asegúrese de que activa la casilla **Cifrar conexión** .  
  
De forma predeterminada, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] se conecta a **master**. Si especifica una base de datos de usuario, verá solo esa base de datos y sus objetos en el Explorador de objetos. Si se conecta a **master**, podrá ver todas las bases de datos. Para más información, consulte la [Introducción a Microsoft Azure SQL Database](http://go.microsoft.com/fwlink/?LinkId=163948).  
  
**Protocolo de red**  
Seleccione un protocolo de la lista. Los protocolos de cliente disponibles son los que se han configurado con la Configuración de red de cliente en Administración de equipos.  
  
**Tamaño del paquete de red**  
Escriba el tamaño de los paquetes de red que desea enviar. El valor predeterminado es 4096 (bytes).  
  
**Tiempo de espera de la conexión**  
Escriba el número de segundos que hay que esperar a que se establezca una conexión antes de que se agote el tiempo de espera. El valor predeterminado es 15 segundos.  
  
**Tiempo de espera de ejecución**  
Escriba el intervalo de tiempo (en segundos) que hay que esperar antes de que finalice la ejecución de una tarea en el servidor. El valor predeterminado es de cero segundos, que indica que no hay tiempo de espera.  
  
**Cifrar conexión**  
Fuerza el cifrado de la conexión.  
  
**Usar color personalizado**  
Seleccione esta opción para especificar el color de fondo para la barra de estado en una ventana del Editor de consultas de [!INCLUDE[ssDE](../../includes/ssde_md.md)] . Para especificar el color, haga clic en **Seleccionar**. En el cuadro de diálogo **Color** , seleccione un color predefinido en la cuadrícula **Colores básicos** o haga clic en **Definir colores personalizados** para definir y usar un color personalizado.  
  
-   Al especificar un color para una entrada del servidor en el panel del **Explorador de objetos** , ese color se usa al abrir una ventana del Editor de consultas. Para abrir una ventana del Editor de consultas, haga clic con el botón derecho en la entrada de servidor y seleccione **Nueva consulta**o, cuando el panel del **Explorador de objetos** esté activo y centrado en este servidor, haga clic en **Nueva consulta** en la barra de herramientas.  
  
-   Al especificar un color para una entrada del servidor en el panel **Servidores registrados** , ese color se usa al abrir una ventana del Editor de consultas. Para abrir una ventana del Editor de consultas, haga clic con el botón derecho en la entrada de servidor y seleccione **Nueva consulta**o, cuando el panel **Servidor registrado** esté activo y centrado en este servidor, haga clic en **Nueva consulta** en la barra de herramientas.  
  
-   En el menú **Archivo** , al hacer clic en **Nuevo** y después en **Consulta de motor de base de datos**, el color que especifique en el cuadro de diálogo **Conectar con el servidor** se aplicará a esa ventana del Editor de consultas.  
  
**Restablecer todo**  
Reemplaza todos los valores de las propiedades de conexión especificadas manualmente por los valores predeterminados.  
  
**Conectar**  
Intenta establecer una conexión utilizando los valores de la lista.  
  
**Opciones**  
Haga clic aquí para modificar el cuadro de diálogo y ocultar las opciones adicionales de conexión al servidor, como recordar la contraseña.  
  
**Probar**  
Al registrar [!INCLUDE[ssDE](../../includes/ssde_md.md)] en **Servidores registrados**, haga clic para probar la conexión.  
  
**Guardar**  
Guarda la configuración en **Servidores registrados**.  
  
## <a name="see-also"></a>Vea también  
[Cuadro de diálogo Propiedades de conexión](../../ssms/f1-help/connection-properties-dialog-box.md)  
  

