---
title: Propiedad IsSharePointIntegrated (MSReportServer_Instance de WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: e21d00ad-5d9a-4290-8d74-7eeeda39e1ed
caps.latest.revision: 13
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: aa4ae0d920db408fe41fb33a52464fe0b88e8d55
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36103462"
---
# <a name="issharepointintegrated-property-wmi-msreportserverinstance"></a>Propiedad IsSharePointIntegrated (WMI MSReportServer_Instance)
  Especifica si el servidor de informes está en modo integrado de SharePoint. A partir de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], esta propiedad siempre devuelve `False`, porque en modo de SharePoint las instancias de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] son servicios compartidos de SharePoint y los proveedores WMI no las controlan.  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a>Valores de propiedad  
 Un valor `Boolean` que indica si el servidor de informes está en modo integrado de SharePoint.  
  
## <a name="requirements"></a>Requisitos  
 **Espacio de nombres:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Miembros de MSReportServer_Instance](msreportserver-instance-members.md)   
 [Clase MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
  