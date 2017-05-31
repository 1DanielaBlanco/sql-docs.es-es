---
title: "Lección 1: Creación de cuentas de Windows para replicación | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
- replication [SQL Server], administering
ms.assetid: 65c3816b-47f0-448c-a4a4-ebd3e2a58820
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1c15031eb2b01a47a933d899c045db6a7123676a
ms.contentlocale: es-es
ms.lasthandoff: 04/11/2017

---
# <a name="lesson-1-creating-windows-accounts-for-replication"></a>Lección 1: Crear cuentas de Windows para replicación
En esta lección creará cuentas de Windows para ejecutar agentes de replicación. Creará distintas cuentas de Windows en el servidor local para los siguientes agentes:  
  
|Agente|Ubicación|Nombre de cuenta|  
|---------|------------|----------------|  
|Agente de instantáneas|publicador|\<*nombreDeEquipo*>\repl_snapshot|  
|Agente de registro del LOG|publicador|\<*nombreDeEquipo*>\repl_logreader|  
|Agente de distribución|Publicador y suscriptor|\<*nombreDeEquipo*>\repl_distribution|  
|Agente de mezcla|Publicador y suscriptor|\<*nombreDeEquipo*>\repl_merge|  
  
> [!NOTE]  
> En los tutoriales de replicación, el publicador y el distribuidor comparten la misma instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. El publicador y el suscriptor pueden compartir la misma instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], aunque no es necesario. Si el publicador y el suscriptor comparten la misma instancia, no se requieren los pasos que se utilizan para crear las cuentas en el suscriptor.  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-publisher"></a>Para crear cuentas locales de Windows para agentes de replicación en el publicador  
  
1.  En el publicador, vaya al Panel de control y abra **Administración de equipos** en **Herramientas administrativas** .  
  
2.  En **Herramientas del sistema**, expanda **Usuarios y grupos locales**.  
  
3.  Haga clic con el botón derecho en **Usuarios** y después haga clic en **Usuario nuevo**.  
  
4.  Escriba **repl_snapshot** en el cuadro **Nombre de usuario** , proporcione la contraseña y demás información relevante y, después, haga clic en **Crear** para crear la cuenta repl_snapshot.  
  
5.  Repita el paso anterior para crear las cuentas repl_logreader, repl_distribution y repl_merge.  
  
6.  Haga clic en **Cerrar**.  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-subscriber"></a>Para crear cuentas locales de Windows para agentes de replicación en el suscriptor  
  
1.  En el suscriptor, vaya al Panel de control y abra **Administración de equipos** en **Herramientas administrativas** .  
  
2.  En **Herramientas del sistema**, expanda **Usuarios y grupos locales**.  
  
3.  Haga clic con el botón derecho en **Usuarios** y después haga clic en **Usuario nuevo**.  
  
4.  Escriba **repl_distribution** en el cuadro **Nombre de usuario** , proporcione la contraseña y demás información relevante y, después, haga clic en **Crear** para crear la cuenta repl_distribution.  
  
5.  Repita el paso anterior para crear la cuenta repl_merge.  
  
6.  Haga clic en **Cerrar**.  
  
## <a name="next-steps"></a>Pasos siguientes  
Ha creado correctamente cuentas de Windows para agentes de replicación. A continuación, configurará la carpeta de instantáneas. Consulte [Lección 2: Preparar la carpeta de instantáneas](../../relational-databases/replication/lesson-2-preparing-the-snapshot-folder.md).  
  
## <a name="see-also"></a>Vea también  
[Información general sobre los agentes de replicación](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
  

