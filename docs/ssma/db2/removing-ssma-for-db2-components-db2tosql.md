---
title: "Eliminación de SSMA para los componentes de DB2 (DB2ToSQL) | Documentos de Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 4ee0d698-6246-48eb-b963-d62be81cab6a
caps.latest.revision: "6"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2a7b78b858bc4af9820dd919d46d38e283920c1f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="removing-ssma-for-db2-components-db2tosql"></a>Eliminación de SSMA para los componentes de DB2 (DB2ToSQL)
Cuando termine de migrar bases de datos de DB2 para [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], debe desinstalar los componentes SSMA. Puede desinstalar los componentes de cliente en cualquier momento. Sin embargo, no debe desinstalar el paquete de extensión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] a menos que las bases de datos migrados ya no use las funciones de la **ssma_DB2** esquema de la **sysdb** base de datos.  
  
## <a name="uninstalling-the-ssma-for-db2-client"></a>Desinstalación de SSMA para cliente de DB2  
Puede desinstalar SSMA mediante **agregar o quitar programas**.  
  
**Para desinstalar SSMA**  
  
1.  En el Panel de Control, abra **agregar o quitar programas**.  
  
2.  Seleccione  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant para DB2**y, a continuación, haga clic en **quitar**.  
  
3.  Para confirmar que desea desinstalar SSMA, haga clic en **Sí**.  
  
## <a name="uninstalling-the-extension-pack"></a>Desinstalar el módulo de extensión  
Si está seguro de las bases de datos migradas no usan objetos en el **sysdb.ssma_DB2** esquema, puede quitar el módulo de extensión mediante la eliminación del esquema: ¿no hay es desinstalar Windows  
  
## <a name="see-also"></a>Vea también  
[Instalación de SSMA para DB2 cliente &#40; DB2ToSQL &#41;](../../ssma/db2/installing-ssma-for-db2-client-db2tosql.md)  
[Instalación de componentes SSMA en SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
  
