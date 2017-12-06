---
title: "Métodos de representación y ejecución | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: report-server-web-service
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- rendered reports [Reporting Services]
- reports [Reporting Services], execution options
- methods [Reporting Services], execution options
- methods [Reporting Services], rendering
ms.assetid: 12626aad-f0be-4653-87d0-60eb3a3fff78
caps.latest.revision: "36"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 3adff3b8401c0693174c4ad4739352cabd135e2d
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2017
---
# <a name="rendering-and-execution-methods"></a>Métodos de representación y ejecución
  Puede utilizar estos métodos para administrar la ejecución de elementos, el almacenamiento en memoria caché y la representación de informes.  
  
|Método|Acción|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.FlushCache%2A>|Invalida la memoria caché para un elemento.|  
|<xref:ReportService2010.ReportingService2010.GetCacheOptions%2A>|Devuelve la configuración de la memoria caché para un elemento y la configuración que describe cuándo expira la copia del elemento en la memoria caché.|  
|<xref:ReportService2010.ReportingService2010.GetExecutionOptions%2A>|Devuelve la opción de ejecución y los valores asociados para un elemento individual.|  
|<xref:ReportService2010.ReportingService2010.ListExecutionSettings%2A>|Devuelve una lista de valores de ejecución admitidos.|  
|<xref:ReportExecution2005.ReportExecutionService.Render%2A>|Procesa el informe especificado y lo representa en un formato especificado.|  
|<xref:ReportService2010.ReportingService2010.SetCacheOptions%2A>|Configura un elemento para el almacenamiento en memoria caché y proporciona la configuración que especifica cuándo expira la copia del elemento en la memoria caché.|  
|<xref:ReportService2010.ReportingService2010.SetExecutionOptions%2A>|Establece las opciones de ejecución y las propiedades de ejecución asociadas para un elemento especificado.|  
|<xref:ReportService2010.ReportingService2010.UpdateItemExecutionSnapshot%2A>|Genera una instantánea de ejecución de elemento para un elemento especificado.|  
  
## <a name="see-also"></a>Vea también  
 [Creación de aplicaciones con el servicio web y .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Servicio web del servidor de informes](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Métodos del servicio web del servidor de informes](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [Referencia técnica &#40;SSRS&#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
