---
title: Elemento Security (XMLA) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Security Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.security
- urn:schemas-microsoft-com:xml-analysis#Security
- http://schemas.microsoft.com/analysisservices/2003/engine#Security
helpviewer_keywords:
- Security element
ms.assetid: 0b601f69-d16d-4d10-9361-b8afaa6ed357
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: cd1a4c292c1ac722fd91836b364724a0f59f8168
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="security-element-xmla"></a>Elemento Security (XMLA)
  Especifica cómo hacer una copia o restaurar definiciones de seguridad, como los roles y permisos, durante un [copia de seguridad](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) o [restaurar](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) comando.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <Security>...</Security>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|String (enumeración)|  
|Valor predeterminado|*SkipMembership*|  
|Cardinalidad|0-1: Elemento opcional que puede aparecer solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[Copia de seguridad](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [restaurar](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Elementos secundarios|Ninguno|  
  
## <a name="remarks"></a>Comentarios  
 El **seguridad** elemento determina si las definiciones de seguridad, como los roles y permisos, definidas en una [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de datos se copia o se restauran durante, respectivamente, un **Copia de seguridad** o **restaurar** comando. Este elemento determina también si las cuentas de usuario de Windows y los grupos definidos como miembros de las definiciones de seguridad se incluyen como parte del comando **Backup** o **Restore** .  
  
 El valor de este elemento se limita a una de las cadenas enumeradas en la tabla siguiente.  
  
|Valor|Description|  
|-----------|-----------------|  
|*SkipMembership*|Incluye las definiciones de seguridad, pero excluye la información de suscripción, durante un comando **Backup** o **Restore** .|  
|*CopyAll*|Incluye las definiciones de seguridad y la información de suscripción durante un comando **Backup** o **Restore** .|  
|*IgnoreSecurity*|Excluye las definiciones de seguridad durante un comando **Backup** o **Restore** .|  
  
## <a name="see-also"></a>Vea también  
 [Synchronizesecurity, elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/synchronizesecurity-element-xmla.md)   
 [Propiedades &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

