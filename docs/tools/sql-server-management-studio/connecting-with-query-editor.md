---
title: "Conectar con el Editor de consultas | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 48725f54-a7b6-4b79-948e-965c1fe4eef1
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Conectar con el Editor de consultas
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] permite escribir o editar código sin estar conectado al servidor. Esto puede ser útil cuando el servidor no está disponible o cuando se desea preservar los escasos recursos de la red o el servidor. También puede cambiar la conexión del Editor de consultas a una instancia nueva de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sin abrir una ventana nueva del Editor de consultas o volver a escribir código.  
  
## Escribir código sin conexión  
  
#### Para escribir código sin conexión y conectarse posteriormente a servidores diferentes  
  
1.  En la barra de herramientas de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] , haga clic en **Consulta de motor de base de datos** para abrir el Editor de consultas.  
  
2.  En el cuadro de diálogo **Conectar al motor de base de datos** , haga clic en **Cancelar**. Se abrirá el Editor de consultas y la barra de título indicará que el usuario no está conectado a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  En el panel de código, escriba las instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)] siguientes:  
  
    ```  
    SELECT * FROM Production.Product;  
    GO  
    ```  
  
    En este punto, se puede conectar a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] haciendo clic en **Conectar**, **Ejecutar**, **Analizar** o **Mostrar plan de ejecución estimado**. Todas estas opciones están disponibles en el menú **Consulta**, en la barra de herramientas del Editor de consultas o bien en el menú contextual al hacer clic con el botón derecho en la ventana del Editor de consultas. En esta práctica, se utilizará la barra de herramientas.  
  
4.  En la barra de herramientas, haga clic en el botón **Ejecutar** para abrir el cuadro de diálogo **Conectar al motor de base de datos** .  
  
5.  En el cuadro de texto **Nombre de servidor** , escriba un nombre y, a continuación, haga clic en **Opciones**.  
  
6.  En la lista **Conectar con base de datos** de la pestaña **Propiedades de conexión** , seleccione [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] y, a continuación, haga clic en **Conectar**.  
  
7.  Para abrir otra ventana del Editor de consultas con la misma conexión, haga clic en la opción **Nueva consulta**de la barra de herramientas.  
  
8.  Para cambiar conexiones, haga clic con el botón derecho en la ventana del Editor de consultas, seleccione **Conexión** y, después, haga clic en **Cambiar conexión**.  
  
9. En el cuadro de diálogo **Conectar a SQL Server** , seleccione otra instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si está disponible y, a continuación, haga clic en **Conectar**.  
  
Esta nueva función del Editor de consultas permite ejecutar fácilmente el mismo código en varios servidores. Esto puede resultar útil para realizar tareas de mantenimiento que afecten a servidores similares.  
  
## Siguiente tarea de la lección  
[Agregar sangría](../../tools/sql-server-management-studio/adding-indentation.md)  
  
  
  
