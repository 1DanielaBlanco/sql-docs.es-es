---
title: Instalar SMO | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.prod_service: database-engine
ms.component: smo
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- installing SMO
- SMO [SQL Server], installing
- SQL Server Management Objects, installing
ms.assetid: 140e9971-4940-4866-89b9-5cec938e2a16
caps.latest.revision: 46
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1a684d9a7ca41745c2e6ceb51d585e5420ab6740
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "43098442"
---
#<a name="installing-smo"></a>Instalar SMO

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

Esta página proporciona información sobre cómo instalar SMO para su uso por los requisitos del sistema para que usen SMO y aplicaciones.

## <a name="smo-nuget-package"></a>Paquete de NuGet SMO

A partir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2017 SMO se distribuye como el [Microsoft.SqlServer.SqlManagementObjects](https://www.nuget.org/packages/Microsoft.SqlServer.SqlManagementObjects) paquete NuGet para permitir que los usuarios a desarrollar aplicaciones con SMO.

Esto es un sustituto de SharedManagementObjects.msi, que anteriormente se publicó como parte del Feature Pack de SQL para cada versión de SQL Server. Las aplicaciones que usan SMO deben actualizarse para utilizar el paquete de NuGet en su lugar y serán responsables de garantizar que los archivos binarios se instalan con la aplicación que se desarrolla.

>>[!Important]
>>Como se mencionó en el [archivos y números de versión](files-and-version-numbers.md) página, no debe instalar los ensamblados SMO en la GAC. Si lo hace, podría causar problemas con otras aplicaciones que también usan esas versiones de SMO (por ejemplo, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Studio).

##<a name="installing-the-package"></a>Instalación del paquete

Consulte [NuGet Quick Start - uso de un paquete](https://docs.microsoft.com/nuget/quickstart/use-a-package) para obtener instrucciones y ejemplos de instalación y uso de un paquete de NuGet. 
  
## <a name="system-requirements"></a>Requisitos del sistema
  
 SMO requiere [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.0 se ejecutan, por lo que las aplicaciones que usen, deben asegurarse de que los equipos cliente tengan la versión o superior instalado.
  
