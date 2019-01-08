---
title: Ver o cambiar el nivel de compatibilidad de una base de datos | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- compatibility levels [SQL Server], viewing
- compatibility [SQL Server], databases
- compatibility levels [SQL Server], changing
ms.assetid: 579867ec-57cb-4cb8-af35-9688c1e9e15d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 320b2e33ed1f36ab2e67625047897a5e8710b2c4
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2018
ms.locfileid: "52783757"
---
# <a name="view-or-change-the-compatibility-level-of-a-database"></a>Ver o cambiar el nivel de compatibilidad de una base de datos
  En este tema se describe cómo ver o cambiar el nivel de compatibilidad de una base de datos en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Antes de cambiar el nivel de compatibilidad de una base de datos, debería conocer el impacto que el cambio tendría en las aplicaciones. Para obtener más información, vea [Nivel de compatibilidad de ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Seguridad](#Security)  
  
-   **Para ver o cambiar el nivel de compatibilidad de una base de datos, use:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permissions  
 Requiere el permiso ALTER en la base de datos.  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
  
#### <a name="to-view-or-change-the-compatibility-level-of-a-database"></a>Para ver o cambiar el nivel de compatibilidad de una base de datos  
  
1.  Después de conectarse a la instancia apropiada de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], en el Explorador de objetos, haga clic en el nombre del servidor.  
  
2.  Expanda **Bases de datos**y, en función de la base de datos, seleccione la base de datos de un usuario o expanda **Bases de datos del sistema** y seleccione una base de datos del sistema.  
  
3.  Haga clic con el botón derecho en la base de datos y luego haga clic en **Propiedades**.  
  
     Se abre el cuadro de diálogo **Propiedades de la base de datos** .  
  
4.  En el panel **Seleccionar una página** , haga clic en **Opciones**.  
  
     El nivel de compatibilidad actual se muestra en el cuadro de lista **Nivel de compatibilidad** .  
  
5.  Para cambiar el nivel de compatibilidad, seleccione una opción diferente de la lista. Las opciones son **SQL Server 2008 (100)**, **SQL Server 2012 (110)** o **SQL Server 2014 (120)**.  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
  
#### <a name="to-view-the-compatibility-level-of-a-database"></a>Para ver el nivel de compatibilidad de una base de datos  
  
1.  Conéctese al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**. Este ejemplo devuelve el nivel de compatibilidad de la base de datos [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
```tsql  
USE AdventureWorks2012;  
GO  
SELECT compatibility_level  
FROM sys.databases WHERE name = 'AdventureWorks2012';  
GO  
  
```  
  
#### <a name="to-change-the-compatibility-level-of-a-database"></a>Para cambiar el nivel de compatibilidad de una base de datos  
  
1.  Conéctese al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**. Este ejemplo cambia el nivel de compatibilidad de la [!INCLUDE[ssSampleDBobject](../../includes/sssql14-md.md)].  
  
```tsql  
ALTER DATABASE AdventureWorks2012  
SET COMPATIBILITY_LEVEL = 120;  
GO  
```  
  
  
