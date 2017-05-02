---
title: "Propiedades de la publicación, Particiones de datos | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.datapartitions.f1
ms.assetid: 5869edb7-d05f-495b-b828-b7fd5e828d20
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 50ef9df48b07e6be66798ac2bd5f33dc57fe6a84
ms.lasthandoff: 04/11/2017

---
# <a name="publication-properties-data-partitions"></a>Propiedades de la publicación, Particiones de datos
  La página **Particiones de datos** del cuadro de diálogo **Propiedades de la publicación** le permite definir particiones de datos para publicaciones de combinación que utilizan el filtro con parámetros. Después de definir particiones, puede generar instantáneas para estas particiones, proporcionando distintos conjuntos de datos iniciales para diferentes suscriptores sobre la base de las propiedades de conexión (inicio de sesión o nombre del equipo) de los suscriptores. También puede optar por permitir que los suscriptores soliciten la entrega y la generación de instantáneas si no tienen una instantánea disponible para su partición la primera vez que realizan la sincronización. Para más información, consulte [Create a Snapshot for a Merge Publication with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
## <a name="options"></a>Opciones  
 **Agregar**  
 Haga clic en **Agregar** para definir una partición. En el cuadro de diálogo **Agregar partición de datos** , especifique valores para **HOST_NAME()** o **SUSER_SNAME()**y defina una programación para actualizar las instantáneas.  
  
 **Editar**  
 Seleccione una partición existente en la cuadrícula y haga clic en **Editar** para editarla.  
  
 **Delete**  
 Seleccione una partición existente en la cuadrícula y haga clic en **Eliminar** para eliminarla.  
  
 **Generar instantáneas seleccionadas ahora**  
 Seleccione una o varias particiones en la cuadrícula y haga clic en **Generar instantáneas seleccionadas ahora** para generar instantáneas para estas particiones.  
  
 **Limpiar instantáneas existentes**  
 Seleccione una o varias particiones en la cuadrícula y haga clic en **Limpiar instantáneas existentes** para limpiar las instantáneas de estas particiones.  
  
 **Definir automáticamente una partición y generar una instantánea si es necesario cuando un suscriptor nuevo intente sincronizarse**  
 Seleccione esta opción si desea permitir que los suscriptores soliciten la generación y aplicación de instantáneas. Los suscriptores podrían solicitar esta opción si no tienen una instantánea disponible para su partición la primera vez que realizan la sincronización.  
  
## <a name="see-also"></a>Vea también  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Ver y modificar propiedades de publicación](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)   
 [Publicar datos y objetos de base de datos](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  
