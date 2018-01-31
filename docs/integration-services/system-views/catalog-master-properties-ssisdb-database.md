---
title: catalog.master_properties (base de datos SSISDB) | Microsoft Docs
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00bfa716-5390-48e3-b30c-d954d5e0be47
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a46e7c75cc67eefe81329eebe943fca862dfbb48
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="catalogmasterproperties-ssisdb-database"></a>catalog.master_properties (base de datos SSISDB)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Muestra las propiedades del patrón de escalabilidad horizontal de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].

|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|property_name|**nvarchar(256)**|Nombre de la propiedad del patrón de escalabilidad horizontal.|  
|property_value|**nvarchar(max)**|Valor de la propiedad del patrón de escalabilidad horizontal.|

## <a name="remarks"></a>Notas
Esta vista muestra una fila para cada propiedad del patrón de escalabilidad horizontal. Las propiedades mostradas en esta vista incluyen lo siguiente:

|Nombre de propiedad|Description|  
|-------------------|-----------------| 
|**CLUSTER_LOGDB_SERVER**|Instancia de SQL Server donde se ubica la base de datos de registro.|
|**LAST_ONLINE_TIME**|Última vez que el patrón de escalabilidad horizontal estuvo conectado.|
|**MACHINE_IP**|Dirección IP de la máquina.|
|**MACHINE_NAME**|Nombre del equipo.|
|**MASTER_ADDRESS**|Punto de conexión del patrón de escalabilidad horizontal.|
|**MASTER_SERVICE_PORT**|Puerto del punto de conexión del patrón de escalabilidad horizontal.|
|**SSLCERT_THUMBPRINT**|Huella digital del certificado del patrón de escalabilidad horizontal.|

## <a name="permissions"></a>Permisos
Todos los miembros del rol de base de datos público tienen permiso de lectura para esta vista. 
