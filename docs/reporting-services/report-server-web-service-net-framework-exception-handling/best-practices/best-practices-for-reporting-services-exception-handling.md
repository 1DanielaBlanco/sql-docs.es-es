---
title: "Prácticas recomendadas para la administración de excepciones de Reporting Services | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: exceptions [Reporting Services], best practices
ms.assetid: 72fecf28-f02e-4338-b50f-0b21f520302d
caps.latest.revision: "34"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: c49eb2ee13b36a6cf725a6f164fde1e20257e895
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="best-practices-for-reporting-services-exception-handling"></a>Prácticas recomendadas para la administración de excepciones de Reporting Services
  Al desarrollar aplicaciones de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], hay varias metodologías disponibles para eliminar o reducir la aparición de excepciones. Cuando se producen excepciones, proporcione mensajes de error claros y concisos al usuario, y agregue una administración de excepciones adecuada para evitar que las aplicaciones finalicen inesperadamente.  
  
 Una aplicación que envía solicitudes al servicio web del servidor de informes debería:  
  
-   Evitar producir excepciones impidiendo tantas solicitudes no válidas como sea posible.  
  
-   Detectar las excepciones y, siempre que sea posible, proporcionar código de administración de errores específico.  
  
-   Tratar los casos de error que no inician excepciones.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Tema|Description|  
|-----------|-----------------|  
|[Prevención de solicitudes no válidas](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/preventing-invalid-requests.md)|Describe las técnicas para evitar que las solicitudes que no sean válidas se envíen al servidor de informes.|  
|[Uso de los bloques Try/Catch](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-try-and-catch-blocks.md)|Describe cómo mejorar más la confiabilidad de una aplicación con bloques try/catch.|  
|[Administración de advertencias y casos que no producen excepciones](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/handling-warnings-and-cases-that-do-not-cause-exceptions.md)|Explica cómo controlar los errores que no producen ninguna excepción que se inicie a través de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Uso de la propiedad Detail para administrar errores concretos](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md)|Explica cómo administrar mediante programación errores concretos mediante la propiedad **Detail** del objeto **SoapException**.|  
  
## <a name="see-also"></a>Vea también  
 [Propiedad Detail](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md)   
 [Introducción al control de excepciones en Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Clase SoapException de Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  
