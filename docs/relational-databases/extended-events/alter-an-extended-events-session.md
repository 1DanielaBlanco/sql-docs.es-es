---
title: Modificar una sesión de eventos extendidos | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: xevents
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 114ec05b-7eca-4c87-b276-25e37b84be39
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ae6c9348c139bbec3e37c38590a1687b353a5301
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "43104051"
---
# <a name="alter-an-extended-events-session"></a>Modificar una sesión de eventos extendidos
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Después de crear una sesión de eventos extendidos, puede modificarla según sus necesidades con el **Asistente para eventos extendidos de SQL Server**.  
  
## <a name="before-you-begin"></a>Antes de empezar  
 No puede modificar un destino para las sesiones activas e inactivas, y no puede cambiar las configuraciones de propiedades avanzadas de una sesión activa.  
  
 Puede realizar las siguientes modificaciones en las sesiones de eventos activas e inactivas:  
  
-   Agregar o quitar eventos de la sesión y modificar las configuraciones de eventos como campos, filtros y acciones de eventos.  
  
-   Agregar o quitar un destino de la sesión de eventos.  
  
-   Habilitar la opción **Iniciar la sesión de eventos al iniciar el servidor** .  
  
 Puede realizar las siguientes modificaciones adicionales en una sesión de eventos inactiva:  
  
-   Habilitar la opción **Realizar el seguimiento de la relación entre eventos** .  
  
-   Cambiar la configuración de las propiedades avanzadas.  
  
> [!NOTE]  
>  El **Asistente para eventos extendidos de SQL Server** no admite la modificación de la sesión de eventos.  
  
## <a name="how-to-alter-an-extended-events-session-using-the-sql-server-extended-events-wizard"></a>Cómo modificar una sesión de eventos extendidos con el Asistente para eventos extendidos de SQL Server  
  
-   En el Explorador de objetos, expanda **Administración**, expanda **Eventos extendidos**y, a continuación, expanda **Sesiones**.  
  
-   Haga clic con el botón derecho en la sesión que quiera modificar y luego haga clic en **Propiedades**.  
  
-   En el cuadro de diálogo **Propiedades** , realice los cambios adecuados y, a continuación, haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Ver también  
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-event-session-transact-sql.md)   
 [Crear una sesión de eventos extendidos mediante el Editor de consultas](http://msdn.microsoft.com/library/cba0e02b-b201-4863-bf1b-9164e68e5fa8)  
  
  
