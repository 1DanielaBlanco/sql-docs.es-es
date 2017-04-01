---
title: "Especificar el orden de procesamiento de la mezcla de art&#237;culos de tabla (programaci&#243;n de la replicaci&#243;n con Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "artículos [replicación de SQL Server], orden de procesamiento"
  - "replicación de mezcla [replicación de SQL Server], orden de procesamiento de artículos"
ms.assetid: 9fe576a2-f5fb-4fdf-bd7d-cb322021b669
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Especificar el orden de procesamiento de la mezcla de art&#237;culos de tabla (programaci&#243;n de la replicaci&#243;n con Transact-SQL)
  La replicación de mezcla le permite especificar el orden en el que el Agente de mezcla procesa los artículos durante el proceso de sincronización. Al crear cada artículo, puede asignarle un orden mediante programación utilizando los procedimientos almacenados de replicación. Los artículos se procesan en orden desde el valor menor al mayor. Si existen dos artículos que tienen el mismo valor, se procesan al mismo tiempo. Para obtener más información, consulte [especificar el procesamiento de orden de combinar artículos](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md).  
  
### Para especificar el orden de procesamiento de un nuevo artículo de mezcla  
  
1.  En el publicador de la base de datos de publicación, ejecute [sp_addmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Especifique un valor entero que representa el orden de procesamiento para el artículo de **@processing_order**. Para más información, consulte [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
    > [!NOTE]  
    >  Al crear artículos ordenados, debería dejar huecos entre los valores de orden de los artículos. Esto le permitirá establecer nuevos valores en el futuro con mayor facilidad. Por ejemplo, si tiene tres artículos para el que debe especificar un orden de procesamiento fijo, establezca el valor de **@processing_order** a 10, 20 y 30 en lugar de 1, 2 y 3, respectivamente.  
  
### Para cambiar el orden de procesamiento de un artículo de mezcla  
  
1.  Para determinar el orden de procesamiento de un artículo, ejecute [sp_helpmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md) Tenga en cuenta el valor de **processing_order** conjunto de resultados.  
  
2.  En el publicador de la base de datos de publicación, ejecute [sp_changemergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Especifique un valor de **processing_order** para **@property** y un valor entero que representa el orden de procesamiento de **@value**.  
  
## Vea también  
 [Especificar el orden de procesamiento de los artículos de mezcla](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md)  
  
  