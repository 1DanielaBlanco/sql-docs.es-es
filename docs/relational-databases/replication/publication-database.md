---
title: "Base de datos de publicaciones | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.publicationdatabase.f1"
ms.assetid: a9fafc9b-9963-4b59-97a0-3472158fa665
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Base de datos de publicaciones
  La base de datos de publicaciones es la base de datos del publicador que es el origen de los datos y objetos de base de datos que va a replicar. Deberá habilitar cada base de datos de publicaciones utilizada en la replicación. La base de datos se habilita cuando un miembro del rol fijo del servidor **sysadmin** :  
  
-   Crea una publicación en esa base de datos con el Asistente para nueva publicación.  
  
-   Selecciona la base de datos en el cuadro de diálogo **Propiedades del publicador** .  
  
-   Ejecuta **sp_replicationdboption** y establece la opción **publicar** (para publicaciones transaccionales o de instantáneas) o **publicación de mezcla** (para publicaciones de mezcla) a **True**.  
  
## Opciones  
 **Bases de datos**  
 Seleccione el nombre de la base de datos que contiene los datos o los objetos de base de datos que desea publicar.  
  
## Vea también  
 [Publicar datos y objetos de base de datos](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Crear una publicación](../../relational-databases/replication/publish/create-a-publication.md)   
 [Ver y modificar las propiedades del distribuidor y del publicador](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_replicationdboption & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)  
  
  