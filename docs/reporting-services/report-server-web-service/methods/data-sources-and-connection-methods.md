---
title: "Orígenes de datos y métodos de conexión | Microsoft Docs"
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
- connections [Reporting Services], data sources
- reports [Reporting Services], data
- data sources [Reporting Services], methods
ms.assetid: 50999b52-fc7c-4333-9fb0-d04c37a4c90f
caps.latest.revision: "38"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 2e8039303a6d21a3979a76d1a37aa0e041ba8eaa
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2017
---
# <a name="data-sources-and-connection-methods"></a>Orígenes de datos y métodos de conexión
  Puede utilizar estos métodos para establecer y administrar las credenciales y las conexiones a un origen de datos.  
  
|Método|Acción|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateDataSource%2A>|Crea un nuevo origen de datos en la base de datos del servidor de informes o biblioteca de SharePoint.|  
|<xref:ReportService2010.ReportingService2010.DisableDataSource%2A>|Deshabilita un origen de datos que está habilitado.|  
|<xref:ReportService2010.ReportingService2010.EnableDataSource%2A>|Habilita un origen de datos que está deshabilitado.|  
|<xref:ReportService2010.ReportingService2010.GetDataSourceContents%2A>|Devuelve el contenido de un origen de datos.|  
|<xref:ReportService2010.ReportingService2010.GetItemDataSourcePrompts%2A>|Obtiene los mensajes del origen de datos para un elemento especificado.|  
|<xref:ReportService2010.ReportingService2010.GetItemDataSources%2A>|Devuelve los orígenes de datos para un elemento del catálogo.|  
|<xref:ReportService2010.ReportingService2010.ListDependentItems%2A>|Devuelve una lista de elementos de catálogo que hacen referencia a un elemento de catálogo especificado.|  
|<xref:ReportService2010.ReportingService2010.ListSubscriptionsUsingDataSource%2A>|Devuelve una lista de suscripciones que están asociadas a un origen de datos determinado.|  
|<xref:ReportService2010.ReportingService2010.SetDataSourceContents%2A>|Establece las propiedades de conexión que están asociadas a un origen de datos.|  
|<xref:ReportService2010.ReportingService2010.SetItemDataSources%2A>|Establece los orígenes de datos para un elemento en una base de datos del servidor de informes o biblioteca de SharePoint.|  
|<xref:ReportService2010.ReportingService2010.TestConnectForDataSourceDefinition%2A>|Prueba la conexión para un origen de datos. Este método admite las pruebas directas del origen de datos.|  
|<xref:ReportService2010.ReportingService2010.TestConnectForItemDataSource%2A>|Prueba la conexión para un origen de datos. Este método admite las pruebas de los orígenes de datos publicados que son utilizados por los informes o modelos, y por orígenes de datos compartidos.|  
  
## <a name="see-also"></a>Vea también  
 [Creación de aplicaciones con el servicio web y .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Servicio web del servidor de informes](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Métodos del servicio web del servidor de informes](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [Referencia técnica &#40;SSRS&#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
