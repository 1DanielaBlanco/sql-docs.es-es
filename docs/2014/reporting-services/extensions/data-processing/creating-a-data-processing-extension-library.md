---
title: Crear una biblioteca de extensión de procesamiento de datos | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], namespace assignments
- library [Reporting Services]
- assigning namespaces to extensions
ms.assetid: 82f4b71b-dd39-467d-8d8c-6771eb2b12de
caps.latest.revision: 38
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 15e43e0f62111283aebcb6b0e0c4527464a5d9a1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37329029"
---
# <a name="creating-a-data-processing-extension-library"></a>Crear una biblioteca de extensión de procesamiento de datos
  Cada extensión de procesamiento de datos de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] que cree debe tener asignado un espacio de nombres único e integrarse en un archivo de ensamblado o biblioteca. El nombre exacto del espacio de nombres no es importante, pero debe ser único y no compartirse con ninguna otra extensión. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] utiliza el espacio de nombres <xref:Microsoft.ReportingServices.DataProcessing> para las extensiones de procesamiento de datos que se incluyen con [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Debería crear sus propios espacios de nombres únicos para las extensiones de procesamiento de datos de su compañía.  
  
 En el ejemplo siguiente se muestra el código para iniciar una extensión de procesamiento de datos de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] que utiliza los espacios de nombres que contienen las interfaces de procesamiento de datos y algunas clases de utilidades.  
  
```vb  
Imports System  
Imports Microsoft.ReportingServices.DataProcessing  
Imports Microsoft.ReportingServices.Interfaces  
  
Namespace CompanyName.ExtensionName  
   ...  
```  
  
```csharp  
using System;  
using Microsoft.ReportingServices.DataProcessing;  
using Microsoft.ReportingServices.Interfaces;  
  
namespace CompanyName.ExtensionName  
{  
   ...  
```  
  
 Al compilar una extensión de procesamiento de datos de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], debe proporcionar al compilador una referencia a Microsoft.ReportingServices.Interfaces.dll, porque allí están contenidas las interfaces de extensión de procesamiento de datos. El espacio de nombres <xref:Microsoft.ReportingServices.DataProcessing> es necesario para implementar las interfaces de extensión de procesamiento de datos mientras que el espacio de nombres <xref:Microsoft.ReportingServices.Interfaces> es necesario para implementar la interfaz <xref:Microsoft.ReportingServices.Interfaces.IExtension>. Por ejemplo, si todos los archivos que contienen el código para implementar una extensión de entrega de procesamiento de datos de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] escrita en C# estuvieran en un directorio único con la extensión .cs, el comando siguiente se ejecutaría desde ese directorio para compilar los archivos almacenados en CompanyName.ExtensionName.dll.  
  
```csharp  
csc /t:library /out:CompanyName.ExtensionName.dll *.cs /r:System.dll /r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
 En el ejemplo de código siguiente se muestra el comando que se usaría para los archivos de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] con la extensión .vb.  
  
```vb  
vbc /t:library /out:CompanyName.ExtensionName.dll *.vb /r:System.dll /r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
> [!NOTE]  
>  También puede diseñar, desarrollar y generar su extensión de procesamiento de datos mediante [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. Para obtener más información sobre cómo desarrollar ensamblados en [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], vea la documentación de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de Reporting Services](../reporting-services-extensions.md)   
 [Implementar una extensión de procesamiento de datos](implementing-a-data-processing-extension.md)   
 [Biblioteca de extensiones de Reporting Services](../reporting-services-extension-library.md)  
  
  
