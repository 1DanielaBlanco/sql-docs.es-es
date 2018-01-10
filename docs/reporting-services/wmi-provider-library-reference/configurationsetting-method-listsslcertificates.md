---
title: "Método ListSSLCertificates (MSReportServer_ConfigurationSetting de WMI) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: wmi-provider-library-reference
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListSSLCertificates method
ms.assetid: 88cd0936-b202-4ab8-90f2-d9c3f66d37f4
caps.latest.revision: "12"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c8dd72b7dd49e2955b32f0bcb868e7bb04de6a14
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2018
---
# <a name="configurationsetting-method---listsslcertificates"></a>Método de ConfigurationSetting: ListSSLCertificates
  Devuelve una lista de certificados en el equipo del servidor de informes.  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
Public Sub CreateSSLCertificateBinding (ByRef CertificateHash() as String, _  
    ByRef CertName() as String, ByRef HostName() as String, ByRef Length as Int32, _   
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListSSLCertificates(out string[] CertificateHash,   
    out string[] CertName, out string[] Hostname, out Int32 length,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parámetros  
 *CertificateHash[]*  
 [out] Valores hash del certificado.  
  
 *CertName[]*  
 [out] Nombres del certificado.  
  
 *HostName[]*  
 [out] Nombres de host para los certificados.  
  
 *Longitud*  
 [out] Representa la longitud de las matrices *CertificateHash*, *CertName* y *HostName* .  
  
 *HRESULT*  
 [out] Valor que indica si la llamada se realizó correctamente o no.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve *HRESULT* que indica si la llamada al método se realizó correctamente o no. Un valor de 0 indica que la llamada al método se realizó correctamente; un código de error indica que la llamada no se realizó correctamente.  
  
## <a name="remarks"></a>Notas  
  
## <a name="requirements"></a>Requisitos  
 **Espacio de nombres:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Ver también  
 [Miembros MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
