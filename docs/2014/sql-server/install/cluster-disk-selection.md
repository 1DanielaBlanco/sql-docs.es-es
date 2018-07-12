---
title: Selección de disco de clúster | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- cluster disk selection
ms.assetid: 0d6b863d-5972-4a20-9990-64ee8016fea6
caps.latest.revision: 9
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9635c793b32715e6da68f433e368c8ae1fc28b56
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37157536"
---
# <a name="cluster-disk-selection"></a>Selección de disco en clúster
  Utilice la página **Selección de disco de clúster** del Asistente para la instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para seleccionar el recurso de disco de clúster compartido para el clúster de conmutación por error de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . El disco de clúster es donde se colocarán los datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Un disco de clúster compartido no es un requisito para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] las instalaciones de clúster. Servidor de archivos SMB es un almacenamiento admitido para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] conmutación por error de las instalaciones de clúster y puede especificarse mediante la **motor de base de datos – directorios de datos** página antes de completar la instalación.  
  
> [!WARNING]  
>  Si ha seleccionado Analysis Services para que se instale, debe especificar un disco de clúster compartido.  
>   
>  Si tiene previsto habilitar FILESTREAM en esta instancia de clúster de conmutación por error de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], debe especificar un disco de clúster compartido.  
  
## <a name="options"></a>Opciones  
 **Discos compartidos**  
 Seleccione un disco único en la lista. El disco de clúster es donde se colocarán los datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Solo puede especificarse un disco. Si selecciona el grupo que contiene el recurso de quórum de clúster, se mostrará un mensaje de advertencia. Se recomienda no realizar la instalación en el recurso de quórum de clúster.  
  
 **Discos compartidos disponibles**  
 Muestra una lista de los discos disponibles, si cada uno está calificado como disco compartido, y una descripción de cada recurso de disco.  
  
  
