---
title: Configurar el Diseñador de diagramas de base de datos (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.InstallSqlDiagramSupport
helpviewer_keywords:
- Database Diagram Designer
- database diagrams [SQL Server], Database Diagram Designer
- diagrams [SQL Server], Database Diagram Designer
ms.assetid: 927321ee-b459-4f5b-9719-4a7a95639143
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 62add06b58d33af4f2e09ee02322a2cec5a9949b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48108925"
---
# <a name="set-up-database-diagram-designer-visual-database-tools"></a>Configurar el Diseñador de diagramas de base de datos (Visual Database Tools)
  Para usar el diseñador de diagramas de base de datos, un miembro del rol **db_owner** debe configurarlo primero para controlar el acceso a los diagramas.  
  
### <a name="to-set-up-database-diagramming"></a>Para configurar diagramas de base de datos  
  
1.  En el Explorador de objetos, expanda un nodo de base de datos.  
  
2.  Expanda el nodo de Diagramas de base de datos bajo la conexión de bases de datos.  
  
3.  Seleccione **Sí** cuando se le pregunte si desea configurar la creación de diagramas de base de datos.  
  
    > [!NOTE]  
    >  De esta forma creará la tabla de diagrama de base de datos, los procedimientos almacenados del sistema y una función del sistema en la base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
4.  Visual Studio creará los siguientes objetos en la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    1.  sysdiagrams - Tabla  
  
    2.  sp_alterdiagam - Procedimiento almacenado  
  
    3.  sp_creatediagram - Procedimiento almacenado  
  
    4.  sp_dropdiagram - Procedimiento almacenado  
  
    5.  sp_renamediagram - Procedimiento almacenado  
  
    6.  fn_diagramobjects - Función  
  
    7.  sp_helpdiagrams - Procedimiento almacenado  
  
    8.  sp_helpdiagramsdefinition - Procedimiento almacenado  
  
    9. sp_upgraddiagrams - Procedimiento almacenado  
  
## <a name="see-also"></a>Vea también  
 [Descripción de la propiedad del diagrama de base de datos &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Actualizar diagramas de base de datos de ediciones anteriores &#40;Visual Database Tools&#41;](upgrade-database-diagrams-from-previous-editions-visual-database-tools.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-authorization-transact-sql)  
  
  
