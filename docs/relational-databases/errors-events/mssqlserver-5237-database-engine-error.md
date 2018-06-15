---
title: MSSQLSERVER_5237 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 5237 (Database Engine error)
ms.assetid: 9ff28935-d1eb-47ee-99b3-1a65cb948ce7
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bb309a33b9c389a46bd869bb05956a4c247a95cf
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2018
ms.locfileid: "34318256"
---
# <a name="mssqlserver5237"></a>MSSQLSERVER_5237
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|5237|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico|DBCC4_INDEXED_VIEW_CHECK_QUERY_FAILED_NO_ERRORCODE|  
|Texto del mensaje|Error de comprobación del conjunto de filas cruzadas de DBCC para el objeto 'NAME' (Id. de objeto O_ID) debido a un error de consulta interno.|  
  
## <a name="explanation"></a>Explicación  
Un error interno ha provocado que DBCC no pueda ejecutar la consulta para comprobar las vistas indizadas.  
  
## <a name="user-action"></a>Acción del usuario  
Vuelva a ejecutar el comando DBCC.  
  
