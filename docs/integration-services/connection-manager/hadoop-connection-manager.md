---
title: "Administrador de conexiones de Hadoop | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.designer.hadoopconn.f1"
ms.assetid: 8bb15b97-9827-46bc-aca6-068534ab18c4
caps.latest.revision: 7
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 7
---
# Administrador de conexiones de Hadoop
  El Administrador de conexiones de Hadoop permite que un paquete SSIS se conecte a un clúster de Hadoop mediante el uso de los valores especificados para las propiedades.  
  
## Configuración del Administrador de conexiones de Hadoop  
  
1.  En el cuadro de diálogo **Agregar administrador de conexiones SSIS** , seleccione **Hadoop**y haga clic en **Agregar**. Se abrirá el cuadro de diálogo **Hadoop Connection Manager Editor** (Editor del Administrador de conexiones de Hadoop).  
  
2.  Seleccione las pestañas **WebHCat** o **WebHDFS** en el panel izquierdo para configurar información relacionada con el clúster de Hadoop.  
  
3.  Si habilita la opción **WebHCat** para invocar un trabajo de Pig o Hive en Hadoop, realice lo siguiente.  
  
    1.  Para **WebHCat Host**(Host de WebHCat), especifique el servidor que hospeda el servicio WebHCat.  
  
    2.  Para **WebHCat Port**(Puerto de WebHCat), escriba el puerto del servicio WebHCat, cuyo valor predeterminado es 50111.  
  
    3.  Seleccione el método **Authentication** (Autenticación) para acceder al servicio WebHCat. Los valores disponibles son **Basic** (Básico) y **Kerberos**.  
  
         ![Hadoop connection manager editor with basic authentication](../../integration-services/connection-manager/media/hadoop-cm-basic.png "Hadoop connection manager editor with basic authentication")  
  
         ![Hadoop connection manager editor with Kerberos authentication](../../integration-services/connection-manager/media/hadoop-cm-kerberos.png "Hadoop connection manager editor with Kerberos authentication")  
  
    4.  Para **WebHCat User**(Usuario de WebHCat), escriba el **usuario** autorizado para acceder a WebHCat.  
  
    5.  Si selecciona la autenticación **Kerberos** , escriba los valores **Password** (Contraseña) y **Domain**(Dominio) del usuario.  
  
4.  Si habilita la opción **WebHDFS** para copiar datos desde o en HDFS, realice lo siguiente.  
  
    1.  Para **WebHDFS Host**(Host de WebHDFS), especifique el servidor que hospeda el servicio WebHDFS.  
  
    2.  Para **WebHDFS Port**(Puerto de WebHDFS), escriba el puerto del servicio WebHDFS, cuyo valor predeterminado es 50070.  
  
    3.  Seleccione el método **Authentication** (Autenticación) para acceder al servicio WebHDFS. Los valores disponibles son **Basic** (Básico) y **Kerberos**.  
  
    4.  Para **WebHDFS User**(Usuario de WebHDFS), escriba el usuario autorizado para acceder a HDFS.  
  
    5.  Si selecciona la autenticación **Kerberos** , escriba los valores **Password** (Contraseña) y **Domain**(Dominio) del usuario.  
  
5.  Haga clic en **Probar conexión** para probar la conexión. (Solo se prueba la conexión habilitada).  
  
6.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo.  
  
## Vea también  
 [Tarea de Hive de Hadoop](../../integration-services/control-flow/hadoop-hive-task.md)   
 [Tarea de Pig con Hadoop](../../integration-services/control-flow/hadoop-pig-task.md)   
 [Tarea Sistema de archivos de Hadoop](../../integration-services/control-flow/hadoop-file-system-task.md)  
  
  