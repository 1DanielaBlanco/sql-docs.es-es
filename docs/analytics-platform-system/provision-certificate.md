---
title: Certificado PDW aprovisionamiento (Analytics Platform System)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: ''
ms.technology: mpp-data-warehouse
description: La página de aprovisionamiento de certificados de PDW de análisis de plataforma de sistema de Configuration Manager importa o quita el certificado utilizado por PDW.
ms.date: 01/05/2017
ms.topic: article
ms.assetid: 0a423b7d-c6ea-45c1-80b0-26758170594c
caps.latest.revision: 22
ms.openlocfilehash: 13e4f6ba3aeb105813ae53eee3a15ce41616273a
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2018
---
# <a name="pdw-certificate-provisioning"></a>Suministro de certificados PDW
El **suministro de certificados de PDW** página de Analytics Platform System**Configuration Manager** importa o quita el certificado utilizado por PDW. 

El uso, un certificado para cifrar las conexiones contribuye a una comunicación segura al nodo de Control a través de los clientes de SQL Server, herramientas que usan los controladores de SQL Server PDW, el [consola de administración de](monitor-the-appliance-by-using-the-admin-console.md), y los servicios de integración de carga. 
  
## <a name="prerequisites"></a>Requisitos previos  
Antes de instalar el certificado, realice lo siguiente:  
  
1.  Obtener un certificado seguro. Si necesita obtener más información acerca de cómo obtener un certificado seguro, póngase en contacto con Microsoft Support.  
  
2.  Guarde el certificado en el nodo de Control en un archivo PFX protegido por contraseña.  
  
## <a name="for-security-reasons-obtain-a-trusted-certificate"></a>Por motivos de seguridad, obtener un certificado de confianza  
PDW de SQL Server admite el uso de un certificado para cifrar las conexiones al nodo de Control; incluidas las conexiones a la **consola de administración de**.  
  
De forma predeterminada, el **consola de administración de** incluye un certificado autofirmado que proporciona privacidad, pero no la autenticación de servidor. Esto puede hacer las comunicaciones sea vulnerable a un ataque de man-in-the-middle. Cuando un usuario se conecta a la consola de administración mediante el certificado autofirmado, Internet Explorer devuelve el error: "Hay un problema con el certificado de seguridad del sitio Web".  
  
Aunque la conexión mediante el certificado autofirmado cifra los datos sobre la marcha entre el cliente y el servidor, la conexión todavía está expuesto a los atacantes.  
  
> [!WARNING]  
> Los administradores del equipo deben adquirir inmediatamente un certificado que se encadena a una entidad de certificación de confianza reconocido por los clientes, con el fin de tener una conexión segura y quitar el error que informa de Internet Explorer.  
  
La ruta de acceso de certificación debe contener el nombre de dominio completo que se asigna para el nodo de Control de dirección IP del clúster (recomendado) o el nombre que los usuarios escriban sus barras de dirección del explorador para tener acceso a la **consola de administración de**.  
  
Usar el sistema de la plataforma de análisis**Configuration Manager** para agregar o quitar el certificado de confianza. Directamente mediante la herramienta de configuración de certificado de servicios de Microsoft Windows HTTP (**winHttpCertCfg.exe**) administrar el certificado no es compatible.  
  
## <a name="import-or-remove-the-certificate"></a>Importar o quitar el certificado  
Las instrucciones siguientes muestran cómo importar o quitar el certificado del dispositivo.  
  
### <a name="to-import-the-certificate"></a>Para importar el certificado  
  
1.  Iniciar el **de Configuration Manager**.  
Para obtener más información, consulte [iniciar el Administrador de configuración &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  

2.  En el panel izquierdo de la **Configuration Manager**, expanda **topología de almacenamiento de datos paralelos**y, a continuación, haga clic en **certificados**.  
  
3.  Seleccione **importar un certificado y configurar el dispositivo para usarlo**y, a continuación, haga clic en **examinar** explorar y seleccionar el archivo de certificado.  
  
4.  Escriba la contraseña para el certificado en el **contraseña** campo.  
  
5.  Haga clic en **aplicar** para configurar el certificado para el dispositivo.  
  
PDW de SQL Server no cifrará la conexión actual utilizando el certificado importado, pero usará el certificado para las conexiones nuevas.  
  
### <a name="to-remove-the-previously-imported-certificate"></a>Para quitar el certificado importado previamente  
  
1.  Iniciar el **de Configuration Manager**. 

<!-- MISSING LINKS
For more information, see [Launch the Configuration Manager &#40;Analytics Platform System&#41;](launch-the-configuration-manager-analytics-platform-system.md).  
-->
  
2.  En el panel izquierdo de la **Configuration Manager**, expanda **topología de almacenamiento de datos paralelos**y, a continuación, haga clic en **certificados**.  
  
3.  Seleccione **quitar cualquier certificado en el dispositivo**.  
  
4.  Haga clic en **aplicar** para quitar el certificado importado anteriormente desde el dispositivo.  
  
SQL Server PDW continuará cifrar las conexiones actuales, pero no usará el certificado que ha quitado para las nuevas conexiones.  
  
![Certificado PDW del dispositivo DWConfig](media/dwconfig-appl-pdw-cert.png "certificado PDW del dispositivo DWConfig")  
  
## <a name="see-also"></a>Vea también  
[Inicie el Administrador de configuración &#40;sistema de la plataforma de análisis&#41;](launch-the-configuration-manager.md)  
