---
title: "Descripción de XML de flujo de trabajo personalizado (Master Data Services) | Documentos de Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: e267e5f4-38bb-466d-82e8-871eabeec07e
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ca6f208bab4ed0b7932d3bd5f7e9a911b8b2c8af
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="create-a-custom-workflow---xml-description"></a>Crear un flujo de trabajo personalizado - descripción en formato XML
  En [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], el servicio de integración de flujos de trabajo MDS de SQL Server llama al método <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> cuando se inicia un flujo de trabajo. Este método recibe los metadatos y los datos del elemento que desencadenó la regla de negocio del flujo de trabajo como un bloque de XML. Por ejemplo de código que implementa un controlador de flujo de trabajo, consulte [ejemplo de flujo de trabajo personalizado &#40; Master Data Services &#41; ](../../master-data-services/develop/create-a-custom-workflow-example.md).  
  
 El ejemplo siguiente es un ejemplo del código XML que se envía al controlador del flujo de trabajo:  
  
```scr  
<ExternalAction>  
  <Type>TEST</Type>  
  <SendData>1</SendData>  
  <Server_URL>This is my test!</Server_URL>  
  <Action_ID>Test Workflow</Action_ID>  
  <Model_ID>5</Model_ID>  
  <Model_Name>Customer</Model_Name>  
  <Entity_ID>34</Entity_ID>  
  <Entity_Name>Customer</Entity_Name>  
  <Version_ID>8</Version_ID>  
  <MemberType_ID>1</MemberType_ID>  
  <Member_ID>12</Member_ID>  
  <MemberData>  
    <ID>12</ID>  
    <Version_ID>8</Version_ID>  
    <ValidationStatus_ID>3</ValidationStatus_ID>  
    <ChangeTrackingMask>0</ChangeTrackingMask>  
    <EnterDTM>2011-02-25T20:16:36.650</EnterDTM>  
    <EnterUserID>2</EnterUserID>  
    <EnterUserName>MyUserName</EnterUserName>  
    <EnterUserMuid>EEF91D48-B673-4D83-B95F-5A363C11DE91</EnterUserMuid>  
    <EnterVersionId>8</EnterVersionId>  
    <EnterVersionName>VERSION_1</EnterVersionName>  
    <EnterVersionMuid>52B788C2-2750-4651-9DB0-2CB05A88AA5A</EnterVersionMuid>  
    <LastChgDTM>2011-02-25T20:16:36.650</LastChgDTM>  
    <LastChgUserID>2</LastChgUserID>  
    <LastChgUserName>MyUserName</LastChgUserName>  
    <LastChgUserMuid>EEF91D48-B673-4D83-B95F-5A363C11DE91</LastChgUserMuid>  
    <LastChgVersionId>8</LastChgVersionId>  
    <LastChgVersionName>VERSION_1</LastChgVersionName>  
    <LastChgVersionMuid>52B788C2-2750-4651-9DB0-2CB05A88AA5A</LastChgVersionMuid>  
    <Name>Test Customer</Name>  
    <Code>TC</Code>  
  </MemberData>  
</ExternalAction>  
```  
  
 En la tabla siguiente se describen algunas de las etiquetas incluidas en este XML:  
  
|Etiqueta|Description|  
|---------|-----------------|  
|\<Tipo >|El texto que escribió en el **tipo de flujo de trabajo** cuadro de texto [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] para identificar qué carga del ensamblado de flujo de trabajo personalizado.|  
|\<SendData >|Un valor booleano que controla el **incluir datos de miembro en el mensaje** checkbox en [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]. Un valor de 1 significa que la \<MemberData > sección se envían; de lo contrario el \<MemberData > no se envía la sección.|  
|< Server_URL >|El texto que escribió en el **sitio de flujo de trabajo** cuadro de texto [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].|  
|< Action_ID >|El texto que escribió en el **nombre de flujo de trabajo** cuadro de texto [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)].|  
|\<MemberData >|Contiene los datos del miembro que desencadenó la acción del flujo de trabajo. Esto solo se incluye si el valor de \<SendData > es 1.|  
|\<Escriba*xxx*>|Este conjunto de etiquetas contiene metadatos sobre la creación del miembro, por ejemplo, cuándo se creó y quién lo creó.|  
|\<LastChg*xxx*>|Este conjunto de etiquetas contiene metadatos sobre el último cambio realizado en el miembro, como cuándo se realizó el cambio y quién lo hizo.|  
|\<Nombre >|Se cambió el primer atributo del miembro. Este miembro de ejemplo contiene únicamente los atributos Name y Code.|  
|\<Código >|Se cambió el siguiente atributo del miembro. Si este miembro de ejemplo contuviera más atributos, se incluirían detrás de este.|  
  
## <a name="see-also"></a>Vea también  
 [Crear un flujo de trabajo personalizado &#40; Master Data Services &#41;](../../master-data-services/develop/create-a-custom-workflow-master-data-services.md)   
 [Ejemplo de flujo de trabajo personalizado &#40; Master Data Services &#41;](../../master-data-services/develop/create-a-custom-workflow-example.md)  
  
  
