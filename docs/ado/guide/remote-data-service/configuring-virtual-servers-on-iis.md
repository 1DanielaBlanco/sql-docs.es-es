---
title: "Configuración de servidores virtuales en IIS | Documentos de Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- virtual servers in RDS [ADO]
ms.assetid: 2b4786c6-40c4-4ce1-9ad4-03df436e0aff
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 838a9ee2dd248a41ecb4874e75b669f9dd4ba51d
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="configuring-virtual-servers-on-iis"></a>Configuración de servidores virtuales en IIS
Al crear servidores virtuales en servicios de Internet Information Server 4.0, los siguientes dos pasos adicionales necesarios para configurar el servidor virtual para trabajar con RDS:  
  
1.  Al configurar el servidor, consulte "Permitir acceso de ejecución".  
  
2.  Mueva msadcs.dll a *vroot*\msadc, donde *vroot* es el directorio principal del servidor virtual.  
  
> [!IMPORTANT]
>  A partir de Windows 8 y Windows Server 2012, componentes de servidor RDS ya no están incluidos en el sistema operativo Windows (consulte Windows 8 y [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) para obtener más detalles). Componentes de cliente RDS se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y tenga previsto modificar las aplicaciones que actualmente la utilizan. Las aplicaciones que utilizan RDS deben migrar a [servicio de datos de WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Vea también  
 [Aspectos básicos de RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


