---
title: Propiedad de base de datos TRUSTWORTHY | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- TRUSTWORTHY database property
ms.assetid: 64b2a53d-4416-4a19-acc0-664a61b45348
caps.latest.revision: 22
author: CarlRabeler
ms.author: carlraba
manager: craigg
ms.openlocfilehash: cdeb7463fc840f99ca2996dc4eae92493d6487d0
ms.sourcegitcommit: 00ffbc085c5a4b792646ec8657495c83e6b851b5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36940961"
---
# <a name="trustworthy-database-property"></a>Propiedad de base de datos TRUSTWORTHY
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La propiedad de base de datos TRUSTWORTHY sirve para indicar si la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] confía en la base de datos y en su contenido. De forma predeterminada, se establece en OFF, pero puede establecerse en ON mediante la instrucción ALTER DATABASE. Por ejemplo, `ALTER DATABASE AdventureWorks2012 SET TRUSTWORTHY ON;`.  
  
> [!NOTE]  
>  Para establecer esta opción, debe ser miembro del rol fijo de servidor **sysadmin** .  
  
 Esta propiedad se puede utilizar para reducir determinadas amenazas que existan como resultado de adjuntar una base de datos que contenga uno de los objetos siguientes:  
  
-   Ensamblados malintencionados con permisos establecidos en EXTERNAL_ACCESS o UNSAFE. Para más información, consulte [CLR Integration Security](../../relational-databases/clr-integration/security/clr-integration-security.md).  
  
-   Módulos malintencionados que se definen para ejecutarse como si se tratase de usuarios con un alto nivel de privilegios. Para obtener más información, vea [EXECUTE AS &#40;cláusula de Transact-SQL&#41;](../../t-sql/statements/execute-as-clause-transact-sql.md).  
  
 Ambas situaciones requieren un nivel específico de privilegios y están protegidas mediante mecanismos apropiados cuando se utilizan en el contexto de una base de datos que ya está adjunta a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sin embargo, si se deja la base de datos sin conexión, un usuario que tenga acceso al archivo de la base de datos podría adjuntarlo a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que desee y agregar contenido malintencionado a la base de datos. Cuando se separan y adjuntan bases de datos en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], se establecen ciertos permisos en los archivos de datos y de registro que restringen el acceso a los archivos de base de datos.  
  
 Puesto que no se puede confiar inmediatamente en una base de datos que se adjunta a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , no se permite a la base de datos el acceso a recursos situados fuera del ámbito de la misma hasta que se marque explícitamente como de confianza. Además, los módulos que se han diseñado para tener acceso a recursos situados fuera de la base de datos, y los ensamblados con permisos EXTERNAL_ACCESS y UNSAFE, tienen requisitos adicionales para ejecutarse correctamente.  
  
## <a name="related-content"></a>Contenido relacionado  
 [Centro de seguridad para el motor de base de datos SQL Server y la base de datos SQL Azure](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
  
