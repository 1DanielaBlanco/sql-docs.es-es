---
title: Conceder privilegios de invitado a un equipo servidor Web | Documentos de Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- guest privileges in RDS [ADO]
ms.assetid: e851a22d-01bc-4eb0-bc42-92b8f65d1c63
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 92d2e20d82f60923381b95e536f3e7ef2b8ae87e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="granting-guest-privileges-to-a-web-server-computer"></a>Conceder privilegios de invitado a un equipo servidor Web
La cuenta anónima de servidor Web (IUSR_*ComputerName*) debe agregarse al grupo local de invitados en el equipo servidor Web para utilizar RDS.  
  
> [!IMPORTANT]
>  A partir de Windows 8 y Windows Server 2012, componentes de servidor RDS ya no están incluidos en el sistema operativo Windows (consulte Windows 8 y [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) para obtener más detalles). Componentes de cliente RDS se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y tenga previsto modificar las aplicaciones que actualmente la utilizan. Las aplicaciones que utilizan RDS deben migrar a [servicio de datos de WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
### <a name="to-grant-guest-privileges-to-a-web-server-computer"></a>Para conceder privilegios de invitado a un equipo servidor Web  
  
1.  En el equipo de Microsoft Windows 2000 Server, haga clic en **iniciar**, seleccione **programas**, seleccione **herramientas administrativas**y, a continuación, haga clic en **equipo Administración**.  
  
2.  En el árbol de consola, en **usuarios y grupos locales**, haga clic en **grupos**.  
  
3.  Seleccione el **invitados** grupo local. Desde el **acción** menú, elija **propiedades**.  
  
4.  En el **propiedades de invitados** cuadro de diálogo, haga clic en **agregar**.  
  
5.  Si la cuenta anónima de servidor Web no aparece en la lista en la **Seleccionar usuarios o grupos** diálogo cuadro, escriba su nombre (IUSR_*ComputerName*) en el cuadro vacío inferior y, a continuación, haga clic en **agregar** .  
  
6.  Haga clic en **Aceptar**.


