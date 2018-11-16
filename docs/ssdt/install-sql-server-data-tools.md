---
title: Instalar SQL Server Data Tools | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.package.stub
ms.assetid: 6f8616cb-9119-42c3-a9b1-936e088763e7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6fe3172d876c7a74a0ad54f25b58e949646c0f74
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51661764"
---
# <a name="install-sql-server-data-tools"></a>Instalar SQL Server Data Tools
En este tema se describe cómo instalar SQL Server Data Tools. Hay actualizaciones de SQL Server Data Tools disponibles en la página de descarga de SQL Server Data Tools ([Install Latest SQL Server Data Tools](https://go.microsoft.com/fwlink/?LinkID=616714)) (Instalar la versión más reciente de SQL Server Data Tools).  
  
Sin importar si usa Visual Studio 2012 o Visual Studio 2013, instale las últimas actualizaciones de SQL Server Data Tools para obtener las características más recientes.  
  
## <a name="sql-server-data-tools-for-visual-studio-2013"></a>SQL Server Data Tools para Visual Studio 2013  
SQL Server Data Tools se incluye en Visual Studio 2013 Express for Web, Visual Studio 2013 Express for desktop, Visual Studio Community 2013 y todos los SKU de pago, incluidos Professional SKU y versiones posteriores. Después de instalar Visual Studio 2013, vaya a Herramientas -> Extensiones y actualizaciones -> Actualizaciones para averiguar si hay una actualización.  
  
## <a name="sql-server-data-tools-for-visual-studio-2012"></a>SQL Server Data Tools para Visual Studio 2012  
SQL Server Data Tools se incluye en la SKU de Visual Studio 2012 Professional o superior. Después de instalar Visual Studio 2012 y la actualización de SQL Server Data Tools de noviembre de 2012 (o posterior), SQL Server Data Tools puede informar cuando haya que instalar una actualización. Para más información, consulte [Cuadro de diálogo Buscar actualizaciones](../ssdt/check-for-updates-dialog-box.md).  
  
Si Visual Studio 2012 no está instalado, SQL Server Data Tools instalará el shell integrado de Visual Studio 2012 y SQL Server Data Tools.  
  
## <a name="administrative-installation-point"></a>Punto de instalación administrativa  
Si necesita instalar SQL Server Data Tools en varios equipos o en equipos sin acceso a Internet, puede crear un diseño de instalación administrativa en un recurso compartido de red o en un medio físico y, a continuación, instalar desde ese punto de instalación.  
  
Para crear un diseño de instalación, descargue SSDTSetup.EXE y ejecútelo con la opción `/layout`*location* para crear un diseño en *ubicación*. Los usuarios podrán entonces ejecutar SSDTSetup.Exe desde *ubicación*.  
  
Para descargar SSDTSetup.exe, vaya a [Install Latest SQL Server Data Tools](https://go.microsoft.com/fwlink/?LinkID=616714), haga clic en el vínculo correspondiente a su versión de Visual Studio y, a continuación, descargue SSDTSetup.exe para su idioma.  
  
