---
title: MSSQLSERVER_5242 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 5242 (Database Engine error)
ms.assetid: 712b1a10-2f87-41df-a111-1ed9f14102d4
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 93707bc81c34fd87f7cf60c2dca8a6b40a61cfa0
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver5242"></a>MSSQLSERVER_5242
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Id. de evento|5242|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico||  
|Texto del mensaje|Se detectó una incoherencia durante una operación interna en la base de datos '%.*ls' (Id.:%d) en la página %S_PGID. Póngase en contacto con el servicio de soporte técnico. Número de referencia %ld.|  
  
## <a name="explanation"></a>Explicación  
Se ha producido una incoherencia estructural en la página de base de datos a la que se hace referencia en el mensaje de error.  
  
## <a name="see-also"></a>Ver también  
[DBCC CHECKDB &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
[Archivos y grupos de archivos de base de datos](~/relational-databases/databases/database-files-and-filegroups.md)  
  
