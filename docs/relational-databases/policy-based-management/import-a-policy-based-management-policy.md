---
title: "Importar una directiva de administración basada en directivas | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Policy-Based Management, import policy
ms.assetid: 850b7ef9-d2b7-4754-bf04-7cb419ffb776
caps.latest.revision: "12"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9d701f5585a7e8e9066e16d1d77aa9432f099d99
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="import-a-policy-based-management-policy"></a>Importar una directiva de administración basada en directivas
  En este tema se describe cómo importar una instancia de directiva de administración basada en directivas en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Limitaciones y restricciones](#Restrictions)  
  
     [Seguridad](#Security)  
  
-   **Para importar una instancia de directiva mediante:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de empezar  
  
###  <a name="Restrictions"></a> Limitaciones y restricciones  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se distribuye con directivas que se pueden utilizar para supervisar una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. De forma predeterminada, estas directivas no se instalan en [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], pero se pueden importar desde la ubicación predeterminada de C:\Archivos de programa\Microsoft SQL Server\###\Tools\Policies\DatabaseEngine\1033 o C:\Archivos de programa (x86)\Microsoft SQL Server\###\Tools\Policies\DatabaseEngine\1033 en las instalaciones de 64 bits.
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 Requiere la pertenencia al rol PolicyAdministratorRole en la base de datos msdb.  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
  
#### <a name="to-import-a-policy-instance"></a>Para importar una instancia de directiva  
  
1.  En el **Explorador de objetos**, haga clic en el signo más para expandir el servidor en que residirá la instancia de directiva recién importada.  
  
2.  Haga clic en el signo más para expandir la carpeta **Administración** .  
  
3.  Haga clic en el signo más para expandir la carpeta **Administración de directivas**.  
  
4.  Haga clic con el botón derecho en la carpeta **Directivas** y seleccione **Importar directiva**.  
  
5.  En el cuadro de diálogo **Importar** , escriba la ruta de acceso y el nombre del archivo, o use el botón Examinar (**...**) para buscar el archivo XML que contiene la directiva y, después, seleccione el archivo. Para obtener más información acerca de las opciones disponibles en el cuadro de diálogo **Importar** , vea [Import Policies Dialog Box](../../relational-databases/policy-based-management/import-policies-dialog-box.md).  
  
6.  Cuando termine, haga clic en **Aceptar**.  
  
  
