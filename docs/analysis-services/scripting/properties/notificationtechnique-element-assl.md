---
title: Elemento NotificationTechnique (ASSL) | Documentos de Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 23b8d193c3039a9606c0d0a0912829534e9673a3
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
ms.locfileid: "34042549"
---
# <a name="notificationtechnique-element-assl"></a>Elemento NotificationTechnique (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Especifica si [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o una aplicación cliente externa procesará las notificaciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<ProactiveCachingBinding>  
   <NotificationTechnique>...</NotificationTechnique>  
</ProactiveCachingBinding>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|String (enumeración)|  
|Valor predeterminado|*Cliente*|  
|Cardinalidad|0-1: Elemento opcional que puede aparecer solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elemento primario|[ProactiveCachingBinding](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md)|  
|Elementos secundarios|Ninguno|  
  
## <a name="remarks"></a>Comentarios  
 El valor de este elemento se limita a una de las cadenas enumeradas en la tabla siguiente.  
  
|Valor|Description|  
|-----------|-----------------|  
|*Cliente*|La aplicación cliente externa procesa la notificación.|  
|*Server*|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] procesa la notificación.|  
  
 El elemento que corresponde al elemento primario de **NotificationTechnique** en el objeto de Analysis Management Objects (AMO) es el modelo <xref:Microsoft.AnalysisServices.ProactiveCachingBinding>.  
  
 La enumeración que corresponde a los valores permitidos para **NotificationTechnique** en el objeto de Analysis Management Objects (AMO) es el modelo <xref:Microsoft.AnalysisServices.NotificationTechnique>.  
  
## <a name="see-also"></a>Vea también  
 [Tipo de datos ProactiveCachingBinding & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/proactivecachingbinding-data-type-assl.md)  
  
  
