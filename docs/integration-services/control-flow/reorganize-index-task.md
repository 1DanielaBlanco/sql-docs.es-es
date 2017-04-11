---
title: "Tarea Reorganizar &#237;ndice | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.reorganizeindextask.f1"
helpviewer_keywords: 
  - "reorganizar índices"
  - "Reorganizar índice, tarea [Integration Services]"
  - "índices [Integration Services]"
ms.assetid: 9ed87861-e5c3-4fcd-8760-d112f4c0af0c
caps.latest.revision: 43
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 43
---
# Tarea Reorganizar &#237;ndice
  La tarea Reorganizar índice reorganiza los índices de las tablas y vistas de bases de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Para obtener más información sobre la administración de índices, vea [Reorganizar y volver a generar índices](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
 Un paquete puede usar la tarea Reorganizar índice para reorganizar los índices de una base de datos individual o de varias bases de datos. Si la tarea solo reorganiza los índices de una base de datos individual, puede elegir las vistas o las tablas cuyos índices reorganiza la tarea. La tarea Reorganizar índice también incluye la opción de compactar datos de objetos grandes. Los datos de objetos grandes son datos con el tipo de datos **image**, **text**, **ntext**, **varchar(max)**, **nvarchar(max)**, **varbinary(max)** o **xml**. Para obtener más información, vea [Tipos de datos &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md).  
  
 La tarea Reorganizar índice encapsula la instrucción ALTER INDEX de Transact-SQL. Si elige compactar datos de objetos grandes, la instrucción utiliza la cláusula REORGANIZE WITH (LOB_COMPACTION = ON); en caso contrario, se establece LOB_COMPACTION en OFF. Para obtener más información, vea [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md).  
  
> [!IMPORTANT]  
>  El tiempo que tarda la tarea en crear la instrucción Transact-SQL que va a ejecutar es proporcional al número de índices reorganizados por la tarea. Si se configura la tarea para reorganizar los índices de todas las tablas y vistas de una base de datos que contiene una gran cantidad de índices, o para reorganizar índices de varias bases de datos, la tarea puede tardar mucho tiempo en generar la instrucción Transact-SQL.  
  
## Configuración de la tarea Reorganizar índice  
 Puede establecer propiedades a través del Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Esta tarea se encuentra en la sección **Tareas del plan de mantenimiento** del **Cuadro de herramientas** , en el Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Para obtener información acerca de las propiedades que puede establecer en el Diseñador [!INCLUDE[ssIS](../../includes/ssis-md.md)] , haga clic en el tema siguiente:  
  
-   [Tarea Reorganizar índice &#40;Plan de mantenimiento&#41;](../../relational-databases/maintenance-plans/reorganize-index-task-maintenance-plan.md)  
  
## Tareas relacionadas  
 Para obtener información sobre cómo establecer estas propiedades en el Diseñador de [!INCLUDE[ssIS](../../includes/ssis-md.md)], vea [Establecer las propiedades de tareas o contenedores](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md).  
  
## Vea también  
 [Tareas de Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Flujo de control](../../integration-services/control-flow/control-flow.md)  
  
  