---
title: Instalar SQL Server Migration Assistant para Access (AccessToSQL) | Documentos de Microsoft
ms.prod: sql
ms.custom: ''
ms.date: 08/15/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- installing SSMA
- instructions, installation
- instructions, upgrade
- licensing SSMA
- prerequisites for installing SSMA
- procedure, installation
- procedure, licensing
- procedure, upgrading
- removing SSMA
- Setup
- uninstalling SSMA
- upgrading SSMA
ms.assetid: dd50eebd-75df-4e0d-8c4d-88b511aae4c7
caps.latest.revision: 31
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 44df200b0b3f24ddcac48e42bfcc33df1b4a2a70
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34773671"
---
# <a name="installing-sql-server-migration-assistant-for-access-accesstosql"></a>Instalar SQL Server Migration Assistant para Access (AccessToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) para el acceso se instala mediante un asistente basado en Windows Installer. Este tema proporciona información sobre los requisitos previos de instalación, un vínculo a la versión más reciente de SSMA e instrucciones para instalar, licencias, desinstalar y actualizar SSMA.  
  
## <a name="prerequisites"></a>Requisitos previos  
Antes de instalar SSMA, asegúrese de que su sistema cumple los requisitos siguientes:  
  
-   Windows 7 o una versión posterior, o Windows Server 2008 o una versión posterior.  
  
-   [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows Installer 3.1 o una versión posterior.  
  
-   El [!INCLUDE[msCoName](../../includes/msconame_md.md)] .NET Framework versión 4.0 o una versión posterior. La versión 4.0 de .NET Framework está disponible en la [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] disco del producto y mediante el uso de información de la [Guía de Microsoft .NET](https://docs.microsoft.com/dotnet/framework/).
  
-   Acceso y permisos suficientes en el equipo que hospeda la instancia de destino [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]base de datos de SQL Azure a la que se va a migrar datos y objetos de base de datos.  
  
-   Microsoft Data Access Object (DAO) versión del proveedor 12.0 o 14.0. Puede instalar al proveedor de DAO de producto de Microsoft Office 2010 o 2007 o descargarlo del sitio web de Microsoft.  
  
-   El SQL Server Native Access Client (SNAC) versión 10.5 y versiones posteriores para la migración a SQL Azure. Puede obtener la última versión de SNAC desde [Feature Pack de Microsoft® SQL Server® 2008 R2](http://go.microsoft.com/fwlink/?LinkId=196940)  
  
-   4 GB de RAM (recomendado).  
  
## <a name="installing-ssma"></a>Instalación de SSMA  
SSMA es una descarga Web. Para descargar la versión más reciente, consulte el [página de descarga de SQL Server Migration Assistant](http://aka.ms/ssmaforaccess).  
  
Después de descargar la versión más reciente, debe extraer los archivos de instalación de para poder instalar SSMA.

> [!IMPORTANT]  
> -   Desinstale todas las versiones anteriores de SSMA para Access antes de instalar la nueva versión.  
  
**Para instalar SSMA**  
  
1.  Haga doble clic en SSMA para Access *n*.msi, donde *n* es el número de compilación.  
  
2.  En la página de bienvenida, haga clic en **siguiente**.  
  
    Si no tiene los requisitos previos instalados, aparece un mensaje que indica que primero debe instalar los componentes necesarios. Asegúrese de que ha instalado todos los requisitos previos y, a continuación, ejecute de nuevo el programa de instalación.  
  
3.  Lea el contrato de licencia para el usuario final; Si los acepta, seleccione **acepto el contrato**y, a continuación, haga clic en **siguiente**.  
  
4.  En la página Elegir tipo de instalación, haga clic en **típica**.  
  
5.  Haga clic en **Instalar**.  
  
La ubicación de instalación predeterminada es C:\Program Files\Microsoft SQL Server Migration Assistant para Access.  
  
## <a name="uninstalling-ssma-for-access"></a>Desinstalación de SSMA para Access  
Desinstalar SSMA mediante **agregar o quitar programas** en el Panel de Control. Tenga en cuenta que al desinstalar el programa no se eliminan los archivos de proyecto SSMA o archivos de registro.  
  
**Para desinstalar SSMA**  
  
1.  Haga clic en **iniciar**, haga clic en **el Panel de Control**y, a continuación, haga clic en **agregar o quitar programas**.  
  
2.  Seleccione **Microsoft SQL Server Migration Assistant para Access**y, a continuación, haga clic en **quitar**.  
  
## <a name="upgrading-to-a-later-version"></a>Actualizar a una versión posterior  
Si desea actualizar a una versión posterior de SSMA para Access, debe desinstalar primero SSMA para Access y, a continuación, instalar la versión más reciente. Siga las instrucciones de desinstalación de SSMA para la sección de acceso para completar este proceso.  
  
Si abre un proyecto creado en una versión anterior de SSMA para Access, SSMA le pregunta si desea convertir el proyecto a la versión más reciente. Haga clic en **Sí** para trabajar con el proyecto en la versión más reciente de SSMA.  
  
## <a name="see-also"></a>Vea también  
[Preparar las bases de datos de acceso para la migración](http://msdn.microsoft.com/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)  
[Migrar bases de datos de Access a SQL Server](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[Vincular las aplicaciones de Access a SQL Server](http://msdn.microsoft.com/82374ad2-7737-4164-a489-13261ba393d4)  
  
