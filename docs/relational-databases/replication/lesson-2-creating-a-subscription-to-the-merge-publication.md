---
title: "Lecci&#243;n 2: Crear una suscripci&#243;n a la publicaci&#243;n de combinaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "replicación [SQL Server], tutoriales"
ms.assetid: 06722baa-9065-443e-b1d5-99036cf89074
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# Lecci&#243;n 2: Crear una suscripci&#243;n a la publicaci&#243;n de combinaci&#243;n
En esta lección, creará una suscripción con [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Luego establecerá los permisos en la base de datos de suscripciones y generará manualmente la instantánea de datos filtrados para la nueva suscripción. Para realizar esta lección es necesario haber completado la lección anterior, [Lección 1: Publicar datos con la replicación de mezcla](../../relational-databases/replication/lesson-1-publishing-data-using-merge-replication.md).  
  
### Para crear la suscripción  
  
1.  Conéctese al suscriptor en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expanda el nodo del servidor, expanda la carpeta **Replicación**, haga clic con el botón derecho en la carpeta **Suscripciones locales** y, después, haga clic en **Nueva suscripción**.  
  
    Se iniciará el Asistente para nueva suscripción.  
  
2.  En la página **Publicación**, haga clic en **Buscar publicador de SQL Server** en la lista **Publicador**.  
  
3.  En el cuadro de diálogo **Conectar al servidor**, escriba el nombre de la instancia del publicador en el cuadro **Nombre del servidor** y, después, haga clic en **Conectar**.  
  
4.  Haga clic en **AdvWorksSalesOrdersMerge** y en **Siguiente**.  
  
5.  En la página Ubicación del Agente de mezcla, haga clic en **Ejecutar cada agente en su suscriptor** y, luego, en **Siguiente**.  
  
6.  En la página Suscriptores, seleccione el nombre de instancia del servidor del suscriptor y, en **Base de datos de suscripciones**, seleccione **<New Database>** en la lista.  
  
7.  En el cuadro de diálogo **Nueva base de datos**, escriba **SalesOrdersReplica** en el cuadro **Nombre de la base de datos**, haga clic en **Aceptar** y, después, haga clic en **Siguiente**.  
  
8.  En la página Seguridad del Agente de mezcla, haga clic en el botón de puntos suspensivos (**…**), escriba \<*nombre_equipo>***\repl_merge** en el cuadro **Cuenta de proceso**, escriba la contraseña de esta cuenta, haga clic en **Aceptar**, en **Siguiente** y, después, otra vez en **Siguiente**.  
  
9. En la página Inicializar suscripciones, seleccione **En la primera sincronización** de la lista **Inicializar cuando**, haga clic en **Siguiente** y, después, otra vez en **Siguiente**.  
  
10. En la página Valores de HOST_NAME, escriba un valor para **adventure-works\pamela0** en el cuadro **Valor de HOST_NAME** y, después, haga clic en **Finalizar**.  
  
11. Haga clic de nuevo en **Finalizar** y, una vez creada la suscripción, haga clic en **Cerrar**.  
  
### Establecer permisos de base de datos en el suscriptor  
  
1.  Conéctese al suscriptor en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expanda **Bases de datos**, **SalesOrdersReplica** y **Seguridad**, haga clic con el botón derecho en **Usuarios** y, después, seleccione **Nuevo usuario**.  
  
2.  En la página **General**, escriba \<*nombre_equipo>***\repl_merge** en el cuadro **Nombre de usuario**, haga clic en el botón de puntos suspensivos (**…**), haga clic en **Examinar**, seleccione \<*nombre_equipo>***\repl_merge**, haga clic en **Aceptar**, en **Comprobar nombres** y luego en **Aceptar**.  
  
3.  En **Pertenencia al rol de la base de datos**, seleccione **db_owner** y haga clic en **Aceptar** para crear el usuario.  
  
### Para crear la instantánea de datos filtrados para la suscripción  
  
1.  Conéctese al publicador en [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expanda el nodo del servidor y luego la carpeta **Replicación** .  
  
2.  En la carpeta **Publicaciones locales**, haga clic con el botón derecho en la publicación **AdvWorksSalesOrdersMerge** y, luego, haga clic en **Propiedades**.  
  
    Se mostrará el cuadro de diálogo **Propiedades de la publicación** .  
  
3.  Seleccione la página **Particiones de datos** y haga clic en **Agregar**.  
  
4.  En el cuadro de diálogo **Agregar partición de datos**, escriba **adventure-works\pamela0** en el cuadro **Valor de HOST_NAME** y, después, haga clic en **Aceptar**.  
  
5.  Seleccione la partición agregada recientemente, haga clic en **Generar instantáneas seleccionadas ahora** y, después, haga clic en **Aceptar**.  
  
## Pasos siguientes  
Ha creado correctamente una suscripción a la publicación de combinación y ha generado la instantánea filtrada para la nueva partición de datos de la suscripción, de manera que esté disponible cuando se inicialice la suscripción. A continuación, concederá derechos al Agente de mezcla en la base de datos de suscripciones y ejecutará el Agente de mezcla para iniciar la sincronización e inicializar la suscripción. Vea [Lección 3: Sincronizar la suscripción con la publicación de combinación](../../relational-databases/replication/lesson-3-synchronizing-the-subscription-to-the-merge-publication.md).  
  
## Vea también  
[Suscribirse a publicaciones](../../relational-databases/replication/subscribe-to-publications.md)  
[Crear una suscripción de extracción](../../relational-databases/replication/create-a-pull-subscription.md)  
[Instantáneas para publicaciones de combinación con filtros con parámetros](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  
  
