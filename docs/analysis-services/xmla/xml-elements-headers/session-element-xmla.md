---
title: Elemento Session (XMLA) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Session Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.session
- http://schemas.microsoft.com/analysisservices/2003/engine#Session
- urn:schemas-microsoft-com:xml-analysis#Session
helpviewer_keywords:
- Session element
ms.assetid: 884ed090-968e-41d3-97e5-6d12787467da
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b0352de12de4e7dcfa9a91115d700d4040dd5daa
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="session-element-xmla"></a>Elemento Session (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Utiliza el encabezado SOAP en un mensaje de solicitud SOAP para identificar una sesión explícita existente en una instancia de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 **Espacio de nombres** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <Session  
         xmlns="urn:schemas-microsoft-com:xml-analysis"  
         SessionId="string" />  
      ...  
   </soap:Header>  
   <soap:Body>  
      ...  
   </soap:Body>  
</soap:Envelope>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|Ninguno|  
|Valor predeterminado|Ninguno|  
|Cardinalidad|0-1: Elemento opcional que puede aparecer solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|Ninguno|  
|Elementos secundarios|Ninguno|  
  
## <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|SessionId|Atributo **String** requerido que identifica la sesión que se va a utilizar. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] utiliza un identificador único global (GUID) para identificar una sesión.|  
  
## <a name="remarks"></a>Comentarios  
 El **sesión** elemento de encabezado identifica una sesión existente explícitamente iniciada en el [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instancia. El elemento **Session** forma parte del encabezado SOAP en los siguientes tipos de mensajes:  
  
-   Una respuesta SOAP que contiene un elemento de encabezado SOAP [BeginSession](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md) .  
  
-   Una solicitud SOAP para identificar la sesión en la que ejecutar el método [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) o el método [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) .  
  
 Un identificador de sesión no garantiza que una sesión continúe siendo válida. La sesión especificada en el elemento **Session** puede expirar. Por ejemplo, una sesión puede expirar si supera el tiempo de espera o se interrumpe la conexión asociada a la sesión. Si la sesión expira o deja de ser válida, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] finaliza la sesión y revierte cualquier transacción que esté en curso en ese momento. Cualquier mensaje SOAP enviado con un identificador de sesión que ya no sea válido emitirá un error SOAP que indica que la sesión especificada no se puede encontrar.  
  
 Si un **sesión** elemento no se envía como parte de una solicitud SOAP, el [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instancia iniciará implícitamente una sesión para la duración de la **Discover** o **Execute** llamada al método y, a continuación, finalizará dicha sesión una vez completada la llamada al método.  
  
## <a name="see-also"></a>Vea también  
 [EndSession, elemento & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)   
 [Administrar las conexiones y sesiones & #40; XMLA & #41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Encabezados & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
