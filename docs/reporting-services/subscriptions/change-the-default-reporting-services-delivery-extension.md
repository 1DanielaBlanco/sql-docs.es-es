---
title: "Cambiar la extensi&#243;n de entrega predeterminada de Reporting Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Administrador de informes [Reporting Services], extensión de entrega predeterminada"
ms.assetid: 5f6fee72-01bf-4f6c-85d2-7863c46c136b
caps.latest.revision: 19
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 18
---
# Cambiar la extensi&#243;n de entrega predeterminada de Reporting Services
  Puede modificar las opciones de configuración de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] para cambiar la extensión de entrega predeterminada que aparece en la lista **Entregado por** de una página de definición de suscripción. Por ejemplo, puede modificar la configuración de modo que cuando los usuarios creen una nueva suscripción, la entrega de recurso compartido de archivos se seleccione de forma predeterminada en lugar de la entrega por correo electrónico. También puede cambiar el orden en que se muestran las extensiones de entrega en la interfaz de usuario.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]** Modo nativo de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] | Modo de SharePoint de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] incluye las extensiones de entrega Correo electrónico y Recurso compartido de archivos de Windows. El servidor de informes puede tener extensiones de entrega adicionales si ha implementado extensiones personalizadas o de otros fabricantes para admitir la entrega personalizada. La disponibilidad de una extensión de entrega depende de si está implementada en un servidor de informes.  
  
## Configuración predeterminada del servidor de informes de modo nativo  
 El orden en el que una extensión de entrega aparece en el Administrador de informes en la lista **Entregado por** se basa en el orden de las entradas de extensión de entrega del archivo **RSReportServer.config** . Por ejemplo, la siguiente imagen muestra el correo electrónico primero en la lista y está seleccionado de forma predeterminada.  
  
 ![default list of delivery extensions](../../reporting-services/subscriptions/media/ssrs-default-delivery.png "default list of delivery extensions")  
  
 La siguiente es la sección predeterminada de **RSReportServer.config** que controla la extensión de entrega predeterminada y el orden en que se muestran en el Administrador de informes. Tenga en cuenta que el correo electrónico aparece en primer lugar en el archivo y se establece como valor predeterminado.  
  
```  
<DeliveryUI>  
     <Extension Name="Report Server Email" Type="Microsoft.ReportingServices.EmailDeliveryProvider.EmailDeliveryProviderControl,ReportingServicesEmailDeliveryProvider">  
          <DefaultDeliveryExtension>True</DefaultDeliveryExtension>  
               <Configuration>  
               <RSEmailDPConfiguration>  
                    <DefaultRenderingExtension>MHTML</DefaultRenderingExtension>  
               </RSEmailDPConfiguration>  
               </Configuration>  
     </Extension>  
     <Extension Name="Report Server FileShare" Type="Microsoft.ReportingServices.FileShareDeliveryProvider.FileShareUIControl,ReportingServicesFileShareDeliveryProvider"/>  
</DeliveryUI>  
```  
  
#### Configure la entrega de recurso compartido de archivos como la extensión de entrega predeterminada en el Administrador de informes  
  
1.  Los pasos de este procedimiento modifican la configuración para que la entrega de recurso compartido aparece como la primera opción en la interfaz de usuario y es la selección predeterminada.  
  
     Abra el archivo RSReportServer.config en un editor de texto. Para obtener más información acerca del archivo de configuración, consulte [RsReportServer.config Configuration File](../../reporting-services/report-server/rsreportserver-config-configuration-file.md). Después de que cambie la configuración, la interfaz de usuario será similar a la siguiente imagen:  
  
     ![modified list of delivery extensions](../../reporting-services/subscriptions/media/ssrs-modified-delivery.png "modified list of delivery extensions")  
  
2.  Modifique la sección DeliveryUI para que el aspecto sea como en el ejemplo siguiente y tenga en cuenta los cambios clave de:  
  
    1.  La extensión de recurso compartido de archivos está antes de la extensión de correo electrónico. Esto cambiará el orden en que las extensiones aparecen en el Administrador de informes.  
  
    2.  La extensión de recurso compartido de archivos contiene la etiqueta DefaultExtension `<DefaultDeliveryExtension>True</DefaultDeliveryExtension>` y se agregó la etiqueta de cierre de extensión `</Extension>`.  
  
    3.  La extensión de correo electrónico ya no está configurada como el valor predeterminado. `<DefaultDeliveryExtension>False</DefaultDeliveryExtension>`  
  
    ```  
    <DeliveryUI>  
         <Extension Name="Report Server FileShare" Type="Microsoft.ReportingServices.FileShareDeliveryProvider.FileShareUIControl,ReportingServicesFileShareDeliveryProvider">  
              <DefaultDeliveryExtension>True</DefaultDeliveryExtension>  
         </Extension>  
         <Extension Name="Report Server Email" Type="Microsoft.ReportingServices.EmailDeliveryProvider.EmailDeliveryProviderControl,ReportingServicesEmailDeliveryProvider">  
         <DefaultDeliveryExtension>False</DefaultDeliveryExtension>  
         <Configuration>  
              <RSEmailDPConfiguration>  
                   <DefaultRenderingExtension>MHTML</DefaultRenderingExtension>  
              </RSEmailDPConfiguration>  
         </Configuration>  
         </Extension>  
    </DeliveryUI>  
    ```  
  
3.  Guarde el archivo de configuración.  
  
4.  En pocos minutos el servidor de informes volverá a cargar el archivo de configuración y la nueva configuración surtirá efecto. Puede reiniciar el servicio del servidor de informes para forzar la carga del archivo de configuración.  
  
     Cuando se lee la configuración, se escribe el siguiente evento en el registro de eventos de Windows.  
  
     **Identificador del evento:** 109  
  
     **Origen:** Servicio Servidor de informes de Windows (nombre de instancia)  
  
     Se ha modificado el archivo RSReportServer.config  
  
## Servidores de informes en modo de SharePoint  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] El modo de SharePoint almacena la información de las extensiones en las bases de datos de aplicación de servicio de SharePoint y no en el archivo RsrReportServer.config. En el modo de SharePoint, la configuración de la extensión de entrega se modifica con PowerShell.  
  
#### Configurar la extensión de entrega predeterminada  
  
1.  Abra el **Shell de administración de SharePoint**.  
  
2.  Puede omitir este paso si ya conoce el nombre de su aplicación de servicio de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Use el PowerShell siguiente a la lista de las aplicaciones de servicio de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en la granja de SharePoint.  
  
    ```  
    get-sprsserviceapplication | format-list *  
    ```  
  
3.  Ejecute el PowerShell siguiente para comprobar que la extensión de entrega predeterminada actual para la aplicación de servicio "ssrsapp" de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
    ```  
    $app=get-sprsserviceapplication | where {$_.name -like "ssrsapp*"};Get-SPRSExtension -identity $app | where{$_.ServerDirectivesXML -like "<DefaultDelivery*"} | format-list *  
  
    ```  
  
4.  
  
## Vea también  
 [El archivo de configuración RSReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [El archivo de configuración RSReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Entrega a recursos compartidos de archivos en Reporting Services](../../reporting-services/subscriptions/file-share-delivery-in-reporting-services.md)   
 [Entrega por correo electrónico en Reporting Services](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md)   
 [Configurar un servidor de informes para la entrega de correo electrónico (Administrador de configuración de SSRS)](http://msdn.microsoft.com/es-es/b838f970-d11a-4239-b164-8d11f4581d83)  
  
  