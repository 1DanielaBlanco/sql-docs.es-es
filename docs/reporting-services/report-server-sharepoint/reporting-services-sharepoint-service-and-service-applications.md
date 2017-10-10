---
title: Servicio de SharePoint Services y las aplicaciones de servicio de Reporting | Documentos de Microsoft
ms.custom: 
ms.date: 09/25/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: 3b0351819369c0c17a5f97318b1132c69ec71432
ms.contentlocale: es-es
ms.lasthandoff: 10/06/2017

---
# <a name="reporting-services-sharepoint-service-and-service-applications"></a>Servicio de SharePoint Services y las aplicaciones de servicio de Reporting

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

  Modo de SharePoint se ha diseñado en la arquitectura de servicio de SharePoint y utiliza un servicio de SharePoint y una o varias aplicaciones de servicio. Al crear una aplicación de servicio, el servicio estará disponible y se generará la base de datos de aplicación del servicio. Puede crear varias aplicaciones de servicio de Reporting Services pero una aplicación de servicio es suficiente para la mayor parte de los escenarios de implementación.  

> [!NOTE]
> Integración de Reporting Services con SharePoint ya no está disponible después de SQL Server 2016.
  
## <a name="creating-a-reporting-services-service-application"></a>Crear una aplicación de servicio de Reporting Services

 Puede utilizar Administración Central de SharePoint o scripts de PowerShell para crear las aplicaciones de servicios de Reporting Services. Para obtener más información sobre el uso de Administración Central de SharePoint, vea la sección "Crear una aplicación Reporting Services Service" en [instalar Reporting Services SharePoint Mode for SharePoint 2010](http://msdn.microsoft.com/47efa72e-1735-4387-8485-f8994fb08c8c). Consulte la sección de PowerShell más adelante en este tema para ver un ejemplo de un script de PowerShell para crear aplicaciones de servicio.  
  
## <a name="modify-the-associations-of-the-service-application-with-a-proxy-group"></a>Modificar las asociaciones de la aplicación de servicio con un grupo de servidores proxy

 La nueva página para crear aplicaciones de servicio contiene la sección **Asociación de aplicaciones web**. La sección le permite asociar la aplicación de servicio cuando la cree. Siga los pasos siguientes para cambiar la asociación y asignar una configuración de cliente a la aplicación de servicio. El mismo proceso general se puede usar también para agregar el proxy al grupo predeterminado en lugar de cambiar la asociación de la aplicación de servicio a un grupo personalizado.  
  
1.  En Administración central de SharePoint, en Administración de aplicaciones, haga clic en **Configurar las asociaciones de aplicación de servicio**.  
  
2.  En la página Asociaciones de aplicaciones de servicio, cambie la vista a **Aplicaciones de servicio**.  
  
3.  Busque y haga clic en el nombre de la nueva aplicación de servicio de Reporting Services. Puede hacer clic en el **valor predeterminado** del nombre del grupo de proxy de aplicación para agregar el proxy al grupo predeterminado en lugar de completar los pasos siguientes.  
  
4.  Seleccione **Personalizado** en el cuadro de selección **Editar el siguiente grupo de conexiones**.  
  
5.  Active la casilla correspondiente al proxy y haga clic en **Aceptar**.  
  
## <a name="edit-service-application-properties"></a>Modificar las propiedades de la aplicación de servicio

 Puede volver a abrir la página de propiedades de la aplicación de servicio para modificar las propiedades.  
  
1.  En Administración central de SharePoint, en el grupo Administración de aplicaciones, haga clic en **Administrar aplicaciones de servicio**.  
  
2.  Seleccione la aplicación de servicio haciendo clic en la columna de tipo para seleccionar toda la fila. Si hace clic en el nombre de la aplicación, se abre la página de opciones de administración del servicio en lugar de las propiedades de la aplicación de servicio.  
  
3.  En la cinta de opciones de Aplicaciones de servicio, haga clic en **Propiedades**.  
  
## <a name="create-a-reporting-services-service-application-using-powershell"></a>Crear una aplicación de servicio de Reporting Services mediante PowerShell

 Puede utilizar PowerShell para crear el proxy y la aplicación de servicio. En el ejemplo siguiente se supone que ya sabe qué grupo de aplicaciones desea configurar para usar la aplicación de servicio.  
  
1.  Agregue el objeto de grupo de aplicaciones del nombre del grupo de aplicaciones a una variable que se pasa en la acción Nueva.  
  
    ```  
    $appPoolName = get-spserviceapplicationpool “<application pool name>”  
    ```  
  
2.  Crear la aplicación de servicio con un nombre y un nombre de grupo de aplicaciones que proporcione.  
  
    ```  
    New-SPRSServiceApplication –Name ‘MyServiceApplication’ –ApplicationPool $appPoolName –DatabaseName ‘MyServiceApplicationDatabase’ –DatabaseServer ‘<Server Name>’  
    ```  
  
3.  Obtenga el nuevo objeto de aplicación de servicio y canalice el objeto en cmdlet para canalizar el nuevo proxy.  
  
    ```  
    Get-SPRSServiceApplication –name MyServiceApplication | New-SPRSServiceApplicationProxy “MyServiceApplicationProxy”  
    ```  
  
## <a name="related-tasks"></a>Tareas relacionadas
  
|Tarea|Vínculo|  
|----------|----------|  
|Administre la configuración de la aplicación de servicio.|[Administrar una aplicación de servicio de SharePoint para Reporting Services](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md)|  
|Realizar una copia de seguridad y restauración de la aplicación de servicio y de los componentes relacionados como las claves de cifrado y el proxy.|[Copias de seguridad y restauración de aplicaciones de servicio de SharePoint para Reporting Services](../../reporting-services/report-server-sharepoint/backup-and-restore-reporting-services-sharepoint-service-applications.md)|  

¿Tiene alguna pregunta más? [Puede plantear sus dudas en el foro de Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
