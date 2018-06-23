---
title: Solucionar problemas de trabajos multiservidor que usan servidores proxy | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- proxies [SQL Server Agent], multiserver jobs
- jobs [SQL Server Agent], multiserver jobs using proxies
ms.assetid: fc579bd3-010c-4f72-8b5c-d0cc18a1f280
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c55ff4c050c1df0418d4add5c5b84dec4e609d44
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36203094"
---
# <a name="troubleshoot-multiserver-jobs-that-use-proxies"></a>Solucionar problemas de trabajos multiservidor que usan servidores proxy
  Los trabajos distribuidos que tienen pasos asociados a un proxy se ejecutan en el contexto de la cuenta de proxy del servidor de destino. Si se producen errores en los pasos de trabajo que utilizan cuentas de proxy cuando se descargan desde el servidor maestro, busque en la columna **error_message** de la tabla **sysdownloadlist** de la base de datos **msdb** los siguientes mensajes de error:  
  
-   "Este trabajo requiere una cuenta de proxy, pero la coincidencia de proxy se ha deshabilitado en el servidor de destino."  
  
     Para solucionar este error, establezca la subclave del registro **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.***\<n*>** \SQLServerAgent\AllowDownloadedJobsToMatchProxyName** en **1 (true)**. De forma predeterminada, esta subclave está establecida en **0** (`false`). El valor de **MSSQL.**\<*n*> es el nombre de la instancia; por ejemplo, **MSSQL.1** o **MSSQL.3**.  
  
-   "No se encontró el proxy".  
  
     Para resolver este error, asegúrese de que existe una cuenta de proxy en el servidor de destino con el mismo nombre que la cuenta de proxy del servidor maestro en la que se ejecuta el paso de trabajo.  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Crear un entorno multiservidor](create-a-multiserver-environment.md)  
  
  