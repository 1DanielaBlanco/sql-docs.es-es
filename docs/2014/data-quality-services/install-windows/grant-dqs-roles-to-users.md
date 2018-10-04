---
title: Conceder roles de DQS a los usuarios | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: afb445b5-bdbe-4bfe-844f-344766cdc2b2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 250d45bd6acf2165f922e311931fd5a13f633d9e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218995"
---
# <a name="grant-dqs-roles-to-users"></a>Conceder roles de DQS a los usuarios
  En este tema se describe cómo crear los inicios de sesión de SQL según una entidad de seguridad de Windows y cómo conceder roles de [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) en la base de datos DQS_MAIN.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
-   Debe haber completado la instalación del [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] ejecutando el archivo DQSInstaller.exe. Para obtener más información, vea [Ejecutar DQSInstaller.exe para completar la instalación del servidor de calidad de datos](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
-   La cuenta de usuario de Windows debe ser miembro del rol fijo de servidor adecuado (como securityadmin, serveradmin o sysadmin) para crear el inicio de sesión de SQL y concederle los roles de DQS.  
  
### <a name="to-create-sql-login-and-grant-dqs-roles"></a>Para crear un inicio de sesión de SQL y conceder los roles de DQS  
  
1.  Inicie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
2.  En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expanda la instancia de SQL Server y, a continuación expanda **Seguridad**.  
  
3.  Haga clic con el botón derecho en la carpeta **Seguridad** , seleccione **Nuevo**y, después, haga clic en **Inicio de sesión**.  
  
4.  En el cuadro de diálogo **Inicio de sesión - Nuevo** , especifique el nombre de un usuario de Windows en el cuadro **Nombre de inicio de sesión** , especifique el tipo de autenticación como **Autenticación de Windows**y haga clic en **Buscar** para validar el usuario.  
  
5.  Después de validar el usuario, haga clic en la página **Asignación de usuarios** en el panel izquierdo.  
  
6.  En el panel derecho, active la casilla en la columna **Asignar** para la base de datos **DQS_MAIN** y, después, active la casilla **dqs_administrator**, **dqs_kb_editor**o **dqs_kb_operator** en el panel **Pertenencia al rol de base de datos para: DQS_MAIN** , dependiendo del nivel de acceso necesario para el usuario. Para obtener más información acerca de los tres roles de DQS, vea [DQS Security](../dqs-security.md).  
  
7.  En el cuadro de diálogo **Inicio de sesión – Nuevo** , haga clic en **Aceptar** para aplicar los cambios.  
  
    > [!NOTE]  
    >  Si concede el rol **dqs_administrator** a un usuario, aplica los cambios y, tras ello, vuelve a revisar los permisos de usuario, las otras dos casillas de roles de DQS (**dq_kb_editor** y **dqs_kb_operator**) también se activan.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Intente iniciar sesión en el [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] con la cuenta de usuario de Windows para la que ha creado un inicio de sesión de SQL y a la que ha concedido un rol de DQS.  
  
## <a name="see-also"></a>Vea también  
 [Instalar Data Quality Services](install-data-quality-services.md)   
 [Crear un inicio de sesión](../../relational-databases/security/authentication-access/create-a-login.md)  
  
  
