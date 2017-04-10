---
title: "Tarea Ejecutar instrucci&#243;n T-SQL | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.executetsqlstatementtask.f1"
helpviewer_keywords: 
  - "instrucciones Transact-SQL, SSIS"
  - "instrucciones [Integration Services]"
  - "Ejecutar instrucción T-SQL, tarea [Integration Services]"
ms.assetid: 7e9086ca-d27e-46c0-bfad-d61333ebd55e
caps.latest.revision: 35
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 35
---
# Tarea Ejecutar instrucci&#243;n T-SQL
  La tarea Ejecutar instrucción T-SQL ejecuta instrucciones Transact-SQL. Para más información, vea [Referencia de Transact-SQL &#40;motor de base de datos&#41;](../../t-sql/transact-sql-reference-database-engine.md) y [Consultas de Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-queries.md).  
  
 Esta tarea es similar a la tarea Ejecutar SQL. Sin embargo, la tarea Ejecutar instrucción T-SQL solo admite la versión Transact-SQL del lenguaje SQL, por lo que no se puede usar esta tarea para ejecutar instrucciones en servidores que usen otros dialectos del lenguaje SQL. Si necesita ejecutar consultas con parámetros, guardar los resultados de la consulta en variables o usar expresiones de propiedades, debe usar la tarea Ejecutar SQL en lugar de la tarea Ejecutar instrucción T-SQL. Para más información, consulte [Execute SQL Task](../../integration-services/control-flow/execute-sql-task.md).  
  
## Configuración de la tarea Ejecutar T-SQL  
 Puede establecer propiedades a través del Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Esta tarea se encuentra en la sección **Tareas del plan de mantenimiento** del **Cuadro de herramientas** , en el Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Para obtener más información acerca de las propiedades que puede establecer en el Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] , haga clic en el tema siguiente:  
  
-   [Tarea Ejecutar instrucción T-SQL &#40;Plan de mantenimiento&#41;](../../relational-databases/maintenance-plans/execute-t-sql-statement-task-maintenance-plan.md)  
  
 Para obtener más información sobre cómo establecer estas propiedades en el Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] , haga clic en el siguiente tema:  
  
-   [Establecer las propiedades de tareas o contenedores](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## Vea también  
 [Tareas de Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Flujo de control](../../integration-services/control-flow/control-flow.md)   
 [MERGE en paquetes de Integration Services](../../integration-services/control-flow/merge-in-integration-services-packages.md)  
  
  