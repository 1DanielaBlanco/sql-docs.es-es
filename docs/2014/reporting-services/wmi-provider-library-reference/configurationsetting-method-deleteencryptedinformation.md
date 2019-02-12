---
title: Método DeleteEncryptedInformation (MSReportServer_ConfigurationSetting de WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- DeleteEncryptedInformation (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DeleteEncryptedInformation method
ms.assetid: c14ed187-bdd9-4304-88e3-72072f03c21b
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: a0566d2a271c891aaa85e7624974e7bcd2769891
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2019
ms.locfileid: "56021486"
---
# <a name="deleteencryptedinformation-method-wmi-msreportserverconfigurationsetting"></a>Método DeleteEncryptedInformation (WMI MSReportServer_ConfigurationSetting)
  Elimina la información cifrada de la base de datos del servidor de informes.  
  
## <a name="syntax"></a>Sintaxis  
  
```vb  
Public Sub DeleteEncryptedInformation(ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void DeleteEncryptedInformation(out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Parámetros  
 *HRESULT*  
 [out] Valor que indica si la llamada se realizó correctamente o no.  
  
 *ExtendedErrors[]*  
 [out] Matriz de cadenas que contiene los errores adicionales devueltos por la llamada.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve *HRESULT* que indica si la llamada al método se realizó correctamente o no. Un valor de 0 indica que la llamada al método se realizó correctamente. Un valor distinto de cero indica que se ha producido un error.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se invoca este método, se eliminan los datos siguientes:  
  
-   La información de origen de datos cifrada, incluso el nombre de usuario y contraseña.  
  
-   Los datos de suscripción cifrados utilizando las interfaces de extensión de entrega.  
  
-   Toda la información de la tabla de claves en la base de datos del servidor de informes.  
  
 Una vez invocado este método, el usuario debe inicializar cada equipo que utiliza la base de datos del servidor de informes.  
  
 Llamar al método DeleteEncryptedInformation no afecta al archivo de configuración del servidor de informes.  
  
## <a name="requirements"></a>Requisitos  
 **Espacio de nombres:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Miembros MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
