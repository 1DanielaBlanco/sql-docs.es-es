---
title: Iniciar la utilidad sqlcmd | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00d57437-7a29-4da1-b639-ee990db055fb
caps.latest.revision: 39
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: eb2234b466a41b58cc1dd137950514de4b7aa458
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36196886"
---
# <a name="start-the-sqlcmd-utility"></a>Iniciar la utilidad sqlcmd
  Para empezar a usar `sqlcmd`, primero debe iniciar la utilidad y conectarse a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Puede conectarse a una instancia con nombre o a la instancia predeterminada. El primer paso consiste en iniciar la utilidad `sqlcmd`.  
  
> [!NOTE]  
>  La autenticación de Windows es el modo de autenticación predeterminado para `sqlcmd`. Para usar la autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , debe especificar un nombre de usuario y una contraseña mediante las opciones **-U** y **-P** .  
  
> [!NOTE]  
>  De forma predeterminada, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] se instala como la instancia con nombre **sqlexpress**.  
  
 Si no se ha conectado antes a una instancia del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], quizás tenga que configurar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para que acepte conexiones.  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-default-instance-of-sql-server"></a>Para iniciar la utilidad sqlcmd y conectar con una instancia predeterminada de SQL Server  
  
1.  En el menú **Inicio** , haga clic en **Ejecutar**. En el cuadro **Abrir** , escriba **cmd**y, a continuación, haga clic en **Aceptar** para abrir una ventana del símbolo del sistema.  
  
2.  En el símbolo del sistema, escriba `sqlcmd`.  
  
3.  Presione ENTRAR.  
  
     Ahora tiene una conexión de confianza con la instancia predeterminada de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que se está ejecutando en el equipo.  
  
     **1 >** es el `sqlcmd` símbolo del sistema que especifica el número de línea. Cada vez que presione ENTRAR, el número se incrementará en uno.  
  
4.  Para finalizar la `sqlcmd` sesión, escriba `EXIT` en el `sqlcmd` símbolo del sistema.  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-named-instance-of-sql-server"></a>Para iniciar la utilidad sqlcmd y conectar con una instancia con nombre de SQL Server  
  
1.  Abra un símbolo del sistema ventana y escriba `sqlcmd -S` *myServer\instanceName*. Reemplace *myServer\instanceName* por el nombre del equipo y la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a la que quiera conectarse.  
  
2.  Presione ENTRAR.  
  
     El símbolo del sistema de `sqlcmd` (1>) indica que está conectado con la instancia especificada de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    > [!NOTE]  
    >  Las instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)] escritas están almacenadas en un búfer. Se ejecutan como un lote cuando se encuentra el comando GO.  
  
## <a name="see-also"></a>Vea también  
 [Ejecutar archivos de scripts Transact-SQL mediante sqlcmd](sqlcmd-run-transact-sql-script-files.md)  
  
  