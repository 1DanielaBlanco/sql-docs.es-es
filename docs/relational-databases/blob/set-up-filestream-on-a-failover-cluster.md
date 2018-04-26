---
title: Configurar FILESTREAM en un clúster de conmutación por error | Microsoft Docs
ms.custom: ''
ms.date: 08/26/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: blob
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-blob
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FILESTREAM [SQL Server], setting up on a failover cluster
ms.assetid: 6721f780-20b7-4109-8ddb-ac327310699e
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d738480648fc9427707ca3949672a9311fe5f2e2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="set-up-filestream-on-a-failover-cluster"></a>Configurar FILESTREAM en un clúster de conmutación por error
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  En este tema se describe cómo habilitar FILESTREAM en un clúster de conmutación por error. Antes de probar este procedimiento, debería conocer los [clústeres de conmutación por error](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md) y tener habilitado FILESTREAM. Para obtener información sobre cómo habilitar FILESTREAM, vea [Habilitar y configurar FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md).  
  
### <a name="to-set-up-filestream-on-a-failover-cluster"></a>Para configurar FILESTREAM en un clúster de conmutación por error  
  
1.  Configure el nodo principal para el clúster de conmutación por error.  
  
     Cuando finalice el programa de instalación, habilite FILESTREAM en el nodo principal utilizando **Administrador de configuración de SQL Server**. De este modo habilita la configuración que requiere los privilegios de administrador de Windows. Si se requiere acceso remoto, seleccione **Permitir que los clientes remotos tengan acceso de transmisión por secuencias a los datos de FILESTREAM**. De esta forma creará un recurso de clúster de recurso compartido de archivos.  
  
2.  Configure un nodo pasivo.  
  
     Cuando finalice el programa de instalación, habilite FILESTREAM en el nodo pasivo utilizando **Administrador de configuración de SQL Server**. El nombre que especifica para **Nombre de recurso compartido de Windows** debe ser el mismo en todos los nodos del clúster.  
  
3.  Repita el paso 2 para agregar más nodos pasivos.  
  
4.  Una vez agregados todos los nodos, complete el proceso ejecutando el procedimiento almacenado sp_configure en cada sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
5.  Puede repetir los pasos 2, 3 y 4 para agregar y habilitar nodos adicionales en el clúster en cualquier momento.  
  
## <a name="see-also"></a>Ver también  
 [Opciones de configuración de servidor &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Crear un nuevo clúster de conmutación por error de SQL Server &#40;programa de instalación&#41;](../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md)   
 [Quitar una instancia de clúster de conmutación por error de SQL Server &#40;programa de instalación&#41;](../../sql-server/failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md)   
 [Agregar o quitar nodos en un clúster de conmutación por error de SQL Server &#40;programa de instalación&#41;](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)  
  
  
