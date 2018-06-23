---
title: Propiedades de SQL Server (pestaña alta AlwaysOn disponibilidad) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d8630923-a600-4f1c-aca1-027453a3ec82
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.openlocfilehash: c19735c4cdae900f9d9d05b911e37224a31ddf96
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36113714"
---
# <a name="sql-server-properties-alwayson-high-availability-tab"></a>Propiedades de SQL Server (pestaña Alta disponibilidad de AlwaysOn)
  Use la pestaña **Alta disponibilidad de AlwaysOn** del cuadro de diálogo **Propiedades de SQL Server** del Administrador de configuración de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para habilitar o deshabilitar la característica Grupos de disponibilidad de AlwaysOn de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. La habilitación de los Grupos de disponibilidad de AlwaysOn es un requisito previo para que una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] use los grupos de disponibilidad como solución de alta disponibilidad y recuperación ante desastres.  
  
##  <a name="Prerequisites"></a> Requisitos previos  
 Para tener habilitados los Grupos de disponibilidad de AlwaysOn, una instancia del servidor debe cumplir los requisitos previos siguientes.  
  
-   La instancia de servidor debe residir en un nodo de clústeres de conmutación por error de Windows Server (WSFC).  
  
-   Para pertenecer al mismo grupo de disponibilidad, las instancias deben estar en el mismo clúster de WSFC. Un grupo de disponibilidad no puede abarcar varios clústeres de WSFC.  
  
-   La instancia del servidor debe ejecutar una edición de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que admita [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].  
  
-   Habilite los Grupos de disponibilidad de AlwaysOn para las distintas instancias del servidor de una en una. Después de habilitar los Grupos de disponibilidad de AlwaysOn, espere hasta que se haya reiniciado el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antes de habilitar la instancia del servidor siguiente.  
  
> [!NOTE]  
>  Para más información sobre las características admitidas y sobre los requisitos previos, restricciones y recomendaciones adicionales para [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], vea los Libros en pantalla de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="dialog-options"></a>Opciones del cuadro de diálogo  
 **Nombre del clúster de conmutación por error de Windows**  
 Muestra el nombre del clúster de WSFC en el que el equipo local es un nodo.  
  
 **Habilitar a los grupos de disponibilidad AlwaysOn**  
 Use esta casilla para habilitar o deshabilitar los Grupos de disponibilidad de AlwaysOn en esta instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], tal como se indica a continuación:  
  
-   Si esta casilla está los vacía, los Grupos de disponibilidad de AlwaysOn estarán deshabilitados. Para habilitar los Grupos de disponibilidad de AlwaysOn, seleccione esta casilla, haga clic en **Aceptar**y reinicie manualmente el servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Si esta casilla ya está seleccionada, los Grupos de disponibilidad de AlwaysOn ya están habilitados. Para deshabilitar los Grupos de disponibilidad de AlwaysOn, desactive la casilla y haga clic en **Aceptar**. Esto hace que se reinicie la instancia del servidor.  
  
    > [!TIP]  
    >  Después de deshabilitar los Grupos de disponibilidad de AlwaysOn, debe quitar todas las réplicas disponibilidad locales de la instancia del servidor. Si quita la última réplica de un grupo de disponibilidad determinado, también debe quitar el grupo.  
  
## <a name="uielement-list"></a>Lista de UIElement  
  
> [!NOTE]  
>  Para obtener más información sobre los pasos que se deben seguir después de deshabilitar los Grupos de disponibilidad de AlwaysOn y para obtener información sobre cómo crear y configurar grupos de disponibilidad, vea los Libros en pantalla de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
  