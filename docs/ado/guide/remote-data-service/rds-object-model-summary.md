---
title: Resumen del modelo de objetos de RDS | Documentos de Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RDS objects [ADO], object model summary
- RDS object model [ADO]
ms.assetid: 909f9af7-31db-4eec-ad52-650ce74dac2f
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 09738022f51016f50986e8f6164db87eff24d5f2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="rds-object-model-summary"></a>Resumen del modelo de objetos de RDS
> [!IMPORTANT]
>  A partir de Windows 8 y Windows Server 2012, componentes de servidor RDS ya no están incluidos en el sistema operativo Windows (consulte Windows 8 y [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) para obtener más detalles). Componentes de cliente RDS se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y tenga previsto modificar las aplicaciones que actualmente la utilizan. Las aplicaciones que utilizan RDS deben migrar a [servicio de datos de WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
|Objeto|Description|  
|------------|-----------------|  
|[RDS. Espacio de datos](../../../ado/reference/rds-api/dataspace-object-rds.md)|Este objeto contiene un método para obtener a un servidor proxy. El proxy puede ser el valor predeterminado o un programa de servidor personalizado (objeto comercial). El programa de servidor puede invocarse en Internet, una intranet, una red de área local, o puede ser una biblioteca de vínculos dinámicos local.<br /><br /> El **DataSpace** objeto es seguro para scripting.|  
|[RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|Este objeto representa el programa de servidor predeterminado. Ejecuta el comportamiento predeterminado de RDS datos recuperación y actualización.<br /><br /> El **DataFactory** objeto no es seguro para scripting.|  
|[RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)|Este objeto puede invocar automáticamente el **RDS. DataSpace** y **RDSServer.DataFactory** objetos.<br /><br /> Utilice este objeto para invocar el comportamiento de recuperación y actualización de datos RDS de forma predeterminada.<br /><br /> Este objeto también proporciona los medios para controles visuales tener acceso a la devuelta **Recordset** objeto.<br /><br /> El **DataControl** objeto es seguro para scripting.|  
  
## <a name="see-also"></a>Vea también  
 [Conceptos básicos de RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)   
 [Escenario RDS](../../../ado/guide/remote-data-service/rds-scenario.md)   
 [Tutorial RDS](../../../ado/guide/remote-data-service/rds-tutorial.md)   
 [Seguridad y uso de RDS](../../../ado/guide/remote-data-service/rds-usage-and-security.md)


