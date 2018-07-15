---
title: No se admite en instrucciones CREATE STATISTICS en el modo de compatibilidad de 90 o posterior con filas | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- WITH ROWS in CREATE STATISTICS statement
ms.assetid: 197b2ecf-a1a3-4a3a-a523-a0ee919c1dde
caps.latest.revision: 21
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 98aec243141e642cd0ef77719795490a1333f473
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37294095"
---
# <a name="with-rows-is-not-supported-in-create-statistics-statements-in-the-compatibility-mode-of-90-or-later"></a>No se admite WITH ROW en instrucciones CREATE STATISTICS en el modo de compatibilidad de 90 o superior
  No se admite el uso de WITH ROWS en instrucciones CREATE STATISTICS si se ejecuta [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con el modo de compatibilidad establecido en 90 o más.  
  
## <a name="component"></a>Componente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Acción correctora  
 Modifique las instrucciones CREATE STATISTICS que incluyan WITH ROWS especificando WITH SAMPLE *número* filas, o bien especificando otras opciones que cumplen con la sintaxis documentada. Para obtener más información, vea el tema "CREATE STATISTICS (Transact-SQL) en los libros en pantalla SQL Server.  
  
## <a name="see-also"></a>Vea también  
 [Problemas de actualización de motor de base de datos](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Asesor de actualizaciones de SQL Server 2014 &#91;nuevo&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
