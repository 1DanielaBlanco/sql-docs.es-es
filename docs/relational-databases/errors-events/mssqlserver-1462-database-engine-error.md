---
title: MSSQLSERVER_1462 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 1462 (Database Engine error)
ms.assetid: 680e9c1c-a9d6-4765-b601-956d0a83324c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9465f1c9eef03f1fc1ffa0070cc960cfa05bc657
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver1462"></a>MSSQLSERVER_1462
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|1462|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|DBM_DISABLED_DUE_TO_FAILED_REDO|  
|Texto del mensaje|La creación de reflejo de la base de datos está deshabilitada debido a una operación de puesta al día con errores. No se puede reanudar.|  
  
## <a name="explanation"></a>Explicación  
La creación de reflejo de la base de datos no puede poner al día una entrada de registro en el reflejo.  
  
### <a name="possible-causes"></a>Posibles causas  
La causa más probable es que se haya completado una operación de agregar archivos en la base de datos principal pero que haya generado un error en la base de datos reflejada al ser diferentes los nombres de archivo o estructuras de directorio en el servidor principal y reflejado.  
  
## <a name="user-action"></a>Acción del usuario  
Busque la causa de este error en el registro de errores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Intente resolver la causa y reanude la creación de reflejo de la base de datos.  
  
## <a name="see-also"></a>Vea también  
[Solucionar problemas de configuración de creación de reflejo de la base de datos &#40;SQL Server&#41;](~/database-engine/database-mirroring/troubleshoot-database-mirroring-configuration-sql-server.md)  
  
