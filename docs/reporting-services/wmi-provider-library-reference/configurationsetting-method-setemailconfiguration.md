---
title: "Método SetEmailConfiguration (WMI MSReportServer_ConfigurationSetting) | Documentos de Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SetEmailConfiguration (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetEmailConfiguration method
ms.assetid: b40a2224-2c90-4d32-892f-1fe73a0591ca
caps.latest.revision: 19
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: da1694467a88220546fa8ec8e02ff78564f605ed
ms.contentlocale: es-es
ms.lasthandoff: 08/09/2017

---
# <a name="configurationsetting-method---setemailconfiguration"></a>Método ConfigurationSetting - SetEmailConfiguration
  Configura la extensión de entrega de correo electrónico utilizada por el servidor de informes para enviar el correo electrónico.  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
Public Sub SetEmailConfiguration(ByVal SendUsingSMTPServer As Boolean, _  
    ByVal SMTPServer As String, ByVal SenderEmailAddress As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetEmailConfiguration (Boolean SendUsingSMTPServer,   
   string SMTPServer, string SenderEmailAddress,   
   out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parámetros  
 *SendUsingSMTPServer*  
 Valor booleano que indica si el servidor utilizará el servidor SMTP para enviar el correo electrónico. Este valor solamente se puede establecer en true. El valor predeterminado es false.  
  
 *SMTPServer*  
 Cadena que contiene el nombre o dirección IP de un servidor SMTP.  
  
 *SenderEmailAddress*  
 Dirección de correo electrónico utilizada en el campo 'De:' para los correos electrónicos enviados desde el servidor de informes.  
  
 *HRESULT*  
 [out] Valor que indica si la llamada se realizó correctamente o no.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve *HRESULT* que indica si la llamada al método se realizó correctamente o no. Un valor de 0 indica que la llamada al método se realizó correctamente. Un valor distinto de cero indica que se ha producido un error.  
  
## <a name="remarks"></a>Comentarios  
 Cuando el parámetro *SendUsingSMTPServer* se establece en **true**, la entrada de **SendUsing** en el archivo de configuración del servidor de informes se establece en 1. Cuando *SendUsingSMTPServer* se establece en **false**, la entrada de **SendUsing** no se configura.  
  
 Este método no proporciona una manera para que los usuarios establezcan la entrada de **SendUsing** en el archivo de configuración del servidor de informes en un valor distinto de 1. Para configurar el servidor de informes para algo distinto del correo SMTP, debe modificar manualmente el archivo de configuración.  
  
## <a name="requirements"></a>Requisitos  
 **Namespace:**[!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Miembros MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
