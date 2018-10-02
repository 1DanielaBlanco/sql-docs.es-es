---
title: 'rsInternalError: error de Reporting Services | Microsoft Docs'
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: troubleshooting
ms.topic: conceptual
helpviewer_keywords:
- rsInternalError
ms.assetid: 52613d52-fc78-4870-93f0-7d393ab9c335
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 113321ca016042adfb2c98ef1601f5e27dbd7933
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47825913"
---
# <a name="rsinternalerror---reporting-services-error"></a>rsInternalError - Error de Reporting Services
    
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Identificador del evento|rsInternalError|  
|Origen del evento|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|Componente|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Texto del mensaje|Error interno en el servidor de informes. Vea el registro de errores para obtener más detalles.|  
  
## <a name="explanation"></a>Explicación  
 Se trata de un mensaje de error genérico que suele ir seguido de un error más descriptivo que proporciona más información.  
  
 Los errores internos no son comunes. Si obtiene este error, puede conseguir más información en los registros de seguimiento del servidor de informes. Además, si está ejecutando como administrador local en el mismo equipo en el que se produjo el error, puede ver la pila de llamadas para obtener más información.  
  
## <a name="user-action"></a>Acción del usuario  
 Para determinar la causa específica de este mensaje, revise los archivos de registro del servidor de informes, que se encuentran en \Microsoft SQL Server\MSRS12.\<nombreDeInstancia >\Reporting Services\LogFiles. Para más información, vea [Archivos de registro y orígenes de Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md).  
  
 Para ver la pila de llamadas, haga clic con el botón derecho en la página donde se ha producido el error y seleccione **Ver código fuente**. Esta acción requiere tener permisos de administrador para el mismo equipo en que se produce el error.  
  
 Si no hay información adicional disponible, puede intentar de nuevo la solicitud.  
  
## <a name="internal-only"></a>Solo para uso interno  
  
## <a name="see-also"></a>Ver también  
 [Iniciar y detener el servicio del servidor de informes](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)  
  
  
