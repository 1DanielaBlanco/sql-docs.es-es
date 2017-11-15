---
title: "Database Mail XPs (opción de configuración del servidor) | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Database Mail XPs option
- Database Mail [SQL Server], enabling
ms.assetid: e22c4e63-1792-473b-af11-14a7931ca9ed
caps.latest.revision: "20"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 760edb1f453e9f59d349e2c4d3232f3360b1261d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="database-mail-xps-server-configuration-option"></a>Database Mail XPs (opción de configuración del servidor)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Use la opción **DatabaseMail XPs** para habilitar Correo electrónico de base de datos en este servidor. Los valores posibles son:  
  
-   **0** indica que Correo electrónico de base de datos no está disponible (predeterminado).  
  
-   **1** indica que está disponible Correo electrónico de base de datos.  
  
 La configuración surte efecto inmediatamente, sin necesidad de detener y reiniciar el servidor.  
  
 Tras habilitar Correo electrónico de base de datos, debe configurar una base de datos host de Correo electrónico de base de datos para usar Correo electrónico de base de datos.  
  
 Configurar la base de datos con el **Asistente para configuración del correo electrónico de base de datos** habilita los procedimientos almacenados extendidos de Correo electrónico de base de datos en la base de datos **msdb** . Si usa el **Asistente para configuración del correo electrónico de base de datos**, no tiene que usar el siguiente ejemplo de **sp_configure** .  
  
 Si establece la opción **Database Mail XPs** en 0, impide que se inicie Correo electrónico de base de datos. Si está en ejecución cuando se establece la opción en 0, continúa ejecutándose y enviando correo hasta que permanece inactivo durante el tiempo configurado en la opción **DatabaseMailExeMinimumLifeTime** .  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se habilitan los procedimientos almacenados extendidos de Correo electrónico de base de datos.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Database Mail XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [Correo electrónico de base de datos](../../relational-databases/database-mail/database-mail.md)  
  
  
