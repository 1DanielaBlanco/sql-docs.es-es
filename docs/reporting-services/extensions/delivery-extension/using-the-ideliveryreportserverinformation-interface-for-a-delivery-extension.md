---
title: "Uso de la interfaz IDeliveryReportServerInformation para una extensión de entrega | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: extensions
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- IDeliveryReportServerInformation interface
- delivery extensions [Reporting Services], retrieving report server information
ms.assetid: adbce647-18f3-470c-8114-42f8bcc95dc2
caps.latest.revision: "34"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 69bef74be0fc5c25a47c827fbaa69d6cad6ffbc3
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2018
---
# <a name="using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension"></a>Utilizar la interfaz IDeliveryReportServerInformation para una extensión de entrega
  La interfaz <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> expone varias propiedades que se pueden utilizar para recuperar información sobre un servidor de informes. Puede usar esta información para entregar notificaciones e informes. Al implementar la clase de extensión de entrega, implementa la propiedad <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> cuando lo requiere la interfaz <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension>. La propiedad <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.ReportServerInformation%2A> devuelve un objeto que implementa la interfaz <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation>. En este objeto puede obtener una lista de las extensiones de representación que admite actualmente el servidor de informes.  
  
 El bucle **for** siguiente se podría usar para almacenar una lista de extensiones de representación disponibles actualmente en el servidor de informes en un objeto **ArrayList**.  
  
```vb  
Dim renderFormats As New ArrayList()  
Dim e As Microsoft.ReportingServices.Interfaces.Extension  
For Each e In  ReportServerInformation.RenderingExtension  
   If e.Visible Then  
      renderFormats.Add(e.Name)  
   End If  
Next e  
```  
  
```csharp  
ArrayList renderFormats = new ArrayList();  
foreach (Microsoft.ReportingServices.Interfaces.Extension e in ReportServerInformation.RenderingExtension)  
{   
   if (e.Visible)  
   {  
      renderFormats.Add(e.Name);  
   }  
}  
```  
  
 Para más información sobre la interfaz <xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation>, vea [Uso de la interfaz IDeliveryReportServerInformation para una extensión de entrega](../../../reporting-services/extensions/delivery-extension/using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md).  
  
## <a name="see-also"></a>Ver también  
 <xref:Microsoft.ReportingServices.Interfaces>   
 [Implementar una extensión de entrega](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Biblioteca de extensiones de Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
