---
title: "M&#233;todo ReserveURL (MSReportServer_ConfigurationSetting de WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ReservedURL, método"
ms.assetid: b9008a62-3edd-4f8a-99f2-7598c2133899
caps.latest.revision: 14
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# M&#233;todo ReserveURL (MSReportServer_ConfigurationSetting de WMI)
  Agrega una reserva URL para una aplicación determinada.  
  
## Sintaxis  
  
```vb  
Public Sub ReserveURL(Application as String, _  
    UrlString as String, Lcid as Int32, _   
    ByRef [Error] as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ReserveURL(string Application, string UrlString, int Lcid,   
    out string error, out int HRESULT);  
```  
  
## Parámetros  
 *Aplicación*  
 Nombre de la aplicación para la que se va a reservar la dirección URL.  
  
 *URLString*  
 Dirección URL para la reserva.  
  
 *lcid*  
 Configuración regional que se utilizará para los mensajes de error devueltos.  
  
 *Error*  
 [out] Descripción del error que se produjo.  
  
 *HRESULT*  
 [out] Valor que indica si la llamada se realizó correctamente o no.  
  
## Valor devuelto  
 Devuelve *HRESULT* que indica si la llamada al método se realizó correctamente o no. Un valor de 0 indica que la llamada al método se realizó correctamente; un código de error indica que la llamada no se realizó correctamente.  
  
## Comentarios  
 *UrlString* no incluye el nombre del directorio virtual. El método [SetVirtualDirectory](../../reporting-services/wmi-provider-library-reference/setvirtualdirectory-method-wmi-msreportserver-configurationsetting.md) se proporciona para ese fin.  
  
 Las reservas de dirección URL se crean para la cuenta de servicio de Windows actual. El cambio de la cuenta de servicio de Windows requiere la actualización manual de todas las reservas de dirección URL.  
  
 Este método produce el reciclaje con reinicio de dominios de aplicación de todos los dominios de aplicación. Los dominios de aplicación se reinician una vez completada esta operación.  
  
## Requisitos  
 **Espacio de nombres:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## Vea también  
 [Miembros MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  