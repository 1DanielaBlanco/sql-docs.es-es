---
title: Supervisión del uso del disco | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database monitoring [SQL Server], disk usage
- disks [SQL Server]
- monitoring performance [SQL Server], disk usage
- server performance [SQL Server], disk usage
- monitoring [SQL Server], disk activity
- excess paging [SQL Server]
- tuning databases [SQL Server], disk usage
- I/O [SQL Server], monitoring
- disks [SQL Server], monitoring activity
- isolating disk activity [SQL Server]
- database performance [SQL Server], disk usage
- monitoring server performance [SQL Server], disk usage
ms.assetid: 1525449c-ea7d-4222-b294-1ba1fe99c9ac
caps.latest.revision: 22
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: fcd06bddde4b1c720140da4c4af0cae25ad1a2a9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166948"
---
# <a name="monitor-disk-usage"></a>Supervisar el uso del disco
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usa llamadas de entrada/salida (E/S) del sistema operativo Microsoft Windows para realizar las operaciones de lectura y escritura en el disco. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] administra el momento y el modo en que se realizan las operaciones de E/S de disco, pero el sistema operativo Windows realiza las operaciones de E/S subyacentes. El subsistema de E/S incluye el bus del sistema, tarjetas controladoras de disco, discos, unidades de cinta, la unidad de CD-ROM y muchos otros dispositivos de E/S. La E/S del disco es una causa frecuente de los atascos en un sistema.  
  
 La supervisión de la actividad del disco implica dos aspectos básicos:  
  
-   Supervisar la E/S del disco y detectar la paginación excesiva  
  
-   Aislar la actividad del disco que crea [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
 Para obtener más información, vea [Supervisar el uso del disco](http://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx).  
  
  
