---
title: "M&#233;todo SetVirtualDirectory (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
  - "método SetVirtualDirectory"
ms.assetid: 1a25cb1d-38d5-401a-970b-87b642a780e4
caps.latest.revision: 11
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# M&#233;todo SetVirtualDirectory (WMI MSReportServer_ConfigurationSetting)
  Establece el nombre del directorio virtual para una aplicación dada.  
  
## Sintaxis  
  
```vb  
Public Sub SetVirtualDirectory(ByVal Application As String, _  
    ByVal VirtualDirectory As String, ByVal lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetVirtualDirectory(string Application, string VirtualDirectory,   
       int Lcid,out string Error, out int HRESULT);  
```  
  
## Parámetros  
 *Aplicación*  
 Nombre de la aplicación para la que se establece el directorio virtual.  
  
 *VirtualDirectory*  
 Nombre del directorio virtual.  
  
 *lcid*  
 Identificador de configuración regional para el directorio virtual.  
  
 *Error*  
 [out] Descripción del error que se produjo.  
  
 *HRESULT*  
 [out] Valor que indica si la llamada se realizó correctamente o no.  
  
## Valor devuelto  
 Devuelve *HRESULT* que indica si la llamada al método se realizó correctamente o no. Un valor de 0 indica que la llamada al método se realizó correctamente; un código de error indica que la llamada no se realizó correctamente.  
  
## Comentarios  
 Una aplicación solo puede tener un nombre de directorio virtual para todas las reservas de direcciones URL.  
  
 VirtualDirectory debe cumplir las convenciones de nomenclatura para directorios virtuales. VirtualDirectory no debe ser una cadena vacía ni estar en blanco.  
  
 Actualiza el valor del elemento \Configuration\URLReservations\Application\VirtualDirectory. Se realiza correctamente aunque no se hayan creado todavía reservas de direcciones URL.  
  
## Requisitos  
 **Espacio de nombres:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## Vea también  
 [Miembros MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  