---
title: Ejecutar la aplicación Data Quality Client | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dqs.browseforservers.f1
- sql12.dqs.connecttoserver.f1
ms.assetid: 0b2aa202-7ab2-4c9d-b0f1-802588053a1e
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f7c62f4bbf8861e92cd4aec37622db9121824ff9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36105458"
---
# <a name="run-the-data-quality-client-application"></a>Ejecutar la aplicación Data Quality Client
  Puede utilizar [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) ejecutando [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] e iniciando sesión en un [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].  
  
##  <a name="BeforeYouBegin"></a> Antes de empezar  
  
###  <a name="Prerequisites"></a> Requisitos previos  
 Debe haber completado la instalación del [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] ejecutando el archivo DQSInstaller.exe. Para obtener más información, vea [Ejecutar DQSInstaller.exe para completar la instalación del servidor de calidad de datos](install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permissions  
 Para poder iniciar sesión en [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], es necesario disponer de uno de los tres roles de DQS (dqs_administrator, dqs_kb_editor o dqs_kb_operator) en la base de datos DQS_MAIN.  
  
##  <a name="Run"></a> Ejecutar Data Quality Client  
 Para ejecutar [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] en el equipo en el que se ha instalado, haga lo siguiente:  
  
1.  Haga clic en **Inicio**, seleccione **Todos los programas**, seleccione **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**, seleccione **Data Quality Services**y, por último, haga clic en **Data Quality Client**.  
  
2.  En el cuadro de diálogo **Conectar al servidor** :  
  
    1.  Especifique el servidor al que desea conectar la aplicación [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Seleccione **(LOCAL)** para conectarse con [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] en el equipo local. También puede hacer clic en la flecha hacia abajo y seleccionar **\<Buscar más servidores>** en la red para conectarse a un servidor diferente (o al servidor local basándose en el nombre). Se mostrará el cuadro de diálogo **Buscar servidores** . Puede seleccionar un servidor en la pestaña **Servidores locales** o en la pestaña **Servidores de redes** .  
  
    2.  Si quiere cifrar la transferencia de datos entre [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] y [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], haga clic en **Opciones** y, después, active la casilla **Cifrar conexión**.  
  
3.  Haga clic en **Conectar**.  
  
 Aparece la página de inicio del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Para más información, vea [Página de inicio del cliente de calidad de datos](../../2014/data-quality-services/data-quality-client-home-screen.md).  
  
  