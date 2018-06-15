---
title: Propiedad InternetTimeout (RDS) | Documentos de Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- InternetTimeout property [ADO]
ms.assetid: 4d1c8892-4bbc-4e71-bf4b-ba52c0ea9549
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a95ec64f7ed35ab3701fd0ad286829d9f87bec44
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35288278"
---
# <a name="internettimeout-property-rds"></a>Propiedad InternetTimeout (RDS)
Indica el número de milisegundos que transcurrirán antes agota el tiempo de espera de una solicitud.  
  
> [!IMPORTANT]
>  A partir de Windows 8 y Windows Server 2012, componentes de servidor RDS ya no están incluidos en el sistema operativo Windows (consulte Windows 8 y [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) para obtener más detalles). Componentes de cliente RDS se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y tenga previsto modificar las aplicaciones que actualmente la utilizan. Las aplicaciones que utilizan RDS deben migrar a [servicio de datos de WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="settings-and-return-values"></a>Configuración y valores devueltos  
 Establece o devuelve un **largo** agota el tiempo de espera de valor que representa el número de milisegundos que transcurren antes una solicitud.  
  
## <a name="remarks"></a>Notas  
 Esta propiedad solo se aplica a las solicitudes enviadas con los protocolos HTTP o HTTPS.  
  
 Las solicitudes en un entorno de tres niveles pueden tardar varios minutos en ejecutarse. Utilice esta propiedad para especificar un tiempo adicional para las solicitudes de ejecución prolongada.  
  
## <a name="applies-to"></a>Se aplica a  
  
|||  
|-|-|  
|[Objeto DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[Objeto DataSpace (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)|  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de la propiedad InternetTimeout (VB)](../../../ado/reference/rds-api/internettimeout-property-example-vb.md)   
 [Ejemplo de la propiedad InternetTimeout (VC ++)](../../../ado/reference/rds-api/internettimeout-property-example-vc.md)   
 

