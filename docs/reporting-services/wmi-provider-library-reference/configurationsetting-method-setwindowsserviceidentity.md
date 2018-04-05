---
title: Método SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: ''
ms.component: wmi-provider-library-reference
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetWindowsServiceIdentity method
ms.assetid: 9bbc734c-9e69-48c2-8bec-8abe7c6cc987
caps.latest.revision: 19
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c7c0887b3049f935b5a8cab7649acb7ce8a9f000
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2018
---
# <a name="configurationsetting-method---setwindowsserviceidentity"></a>Método ConfigurationSetting - SetWindowsServiceIdentity
  Ejecuta el servicio de Windows de servidor de informes como el usuario de Windows especificado y concede a esta cuenta suficientes permisos de sistema de archivos para permitir que servidor de informes funcione.  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
Public Sub SetWindowsServiceIdentity(UseBuiltInAccount as Boolean, _  
    Account as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetWindowsServiceIdentity(boolean UseBuiltInAccount,   
    string Account, string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Parámetros  
 *UseBuiltInAccount*  
 Indica si la cuenta especificada es una cuenta de Windows integrada.  
  
 *Cuenta*  
 La cuenta de Windows que se utilizará para ejecutar el servicio de Windows, en formato "DOMAIN\alias."  
  
 *Contraseña*  
 La contraseña de la cuenta.  
  
 *HRESULT*  
 [out] Valor que indica si la llamada se realizó correctamente o no.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve *HRESULT* que indica si la llamada al método se realizó correctamente o no. Un valor de 0 indica que la llamada al método se realizó correctamente. Un valor distinto de cero indica que se ha producido un error.  
  
## <a name="remarks"></a>Notas  
 Cuando el parámetro *UseBuiltInAccount* está establecido en **true** y el servidor de informes se está ejecutando en Microsoft [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] o Windows XP, el valor de los parámetros *Nombre*, *Dominio*y *Contraseña* se omite y se usa la cuenta local del sistema.  
  
 Cuando el parámetro *UseBuiltInAccount* está establecido en **true** y el servidor de informes se está ejecutando en Windows Server 2003, las propiedades *Dominio* y *Contraseña* se omiten y el campo de nombre debe contener "Builtin\NetworkService", "Builtin\System" o "Builtin\LocalService".  
  
 El método SetWindowsServiceIdentity establece los permisos de archivo en los archivos y carpetas en el directorio de instalación del servidor de informes.  
  
 La cuenta especificada en el parámetro *Account* requiere los derechos **LogonAsService** en Windows. El método permite este derecho a la cuenta especificada.  
  
## <a name="requirements"></a>Requisitos  
 **Espacio de nombres:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Ver también  
 [Miembros MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
