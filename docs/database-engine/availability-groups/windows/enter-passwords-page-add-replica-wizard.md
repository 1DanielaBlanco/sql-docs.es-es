---
title: Página Escribir contraseñas (Asistente para agregar réplica) | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.addreplicawizard.enterpasswords.f1
ms.assetid: e69207a0-c5c4-44e4-ae9a-4afbb67251d1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 11b171ef067bd5abdc29d306421b956792f1a55b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47790583"
---
# <a name="enter-passwords-page-add-replica-wizard"></a>Página Escribir contraseñas (Asistente para agregar réplica)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  En este tema de Ayuda se describen las opciones de la página **Escribir contraseñas** . Este tema se aplica al [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] de [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 Si las réplicas que seleccionó en la página **Especificar réplicas** contienen bases de datos que tienen una clave maestra de base de datos, aparecerá la página Escribir contraseñas.  
  
## <a name="enter-passwords-options"></a>Opciones para escribir contraseñas  
 La cuadrícula **Usar bases de datos en esta instancia de SQL Server** muestra cada base de datos de usuario local. Estas son sus columnas:  
  
 **Nombre**  
 Muestra el nombre de una base de datos de usuario local.  
  
 **Tamaño**  
 Muestra el tamaño de la base de datos, si el tamaño está disponible para el asistente.  
  
 **Estado**  
 Indica **Se requiere contraseña** en bases de datos que tienen una clave maestra de base de datos. Después de escribir las contraseñas para las claves maestras de base de datos en la columna **Contraseñas** , haga clic en **Actualizar**. Si ha especificado la contraseña correctamente, la columna **Estado** indica **Password entered**(Contraseña escrita).  
  
 Si la base de datos no tiene una clave maestra de base de datos, el **estado** columna indica **No se necesita contraseña**.  
  
 **Contraseña**  
 Si la columna **Estado** indica **Se requiere contraseña**, escriba la contraseña de la clave maestra de base de datos.  
  
 **Actualizar**  
 Haga clic para actualizar la cuadrícula. Esto es útil después de escribir las contraseñas necesarias.  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Usar el Asistente para agregar una réplica al grupo de disponibilidad &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
## <a name="see-also"></a>Ver también  
 [Requisitos previos, restricciones y recomendaciones para Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
