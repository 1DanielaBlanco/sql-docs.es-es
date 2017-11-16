---
title: "PH timeout (opción de configuración del servidor) | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: TSQL
helpviewer_keywords:
- time limit for protocol handler wait [SQL Server]
- timeout options [SQL Server], ph timeout option
- protocols [SQL Server], timing out
- ph timeout option
ms.assetid: ed19a07c-83fe-4582-9c9e-41b1ce571850
caps.latest.revision: "28"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 118ea83ca4d3268f55a6ec1e0c6db68958dad9f4
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="ph-timeout-server-configuration-option"></a>PH timeout (opción de configuración del servidor)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Use la opción ph timeout para especificar el tiempo, en segundos, que el controlador de protocolo de texto completo debe esperar para conectarse a una base de datos antes de que se agote el tiempo de espera. El valor predeterminado es 60 segundos. Aumente el valor de ph timeout cuando se esté agotando el tiempo de espera de los intentos de conexión debido a problemas de red temporales.  
  
 El controlador de protocolo de texto completo se aloja en el host de demonio de filtro y se utiliza para capturar de SQL Server los datos cuyo índice de texto completo se va a crear. Para obtener más información sobre los componentes de búsqueda de texto completo, vea [Búsqueda de texto completo](../../relational-databases/search/full-text-search.md).  
  
 Al intentar capturar una fila de datos, si el controlador de protocolo no puede conectar con SQL Server dentro del tiempo especificado, notifica un error de tiempo de espera para esa fila. El recopilador de texto completo lo volverá a intentar más tarde. Para obtener más información sobre el recopilador de texto completo, vea [Rellenar índices de texto completo](../../relational-databases/search/populate-full-text-indexes.md).  
  
## <a name="see-also"></a>Vea también  
 [Búsqueda de texto completo](../../relational-databases/search/full-text-search.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Opciones de configuración de servidor &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
