---
title: Cambio de nombre de una base de datos | Microsoft Docs
ms.custom: 
ms.date: 11/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: databases
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- databases [SQL Server], renaming
- renaming databases
ms.assetid: 44c69d35-abcb-4da3-9370-5e0bc9a28496
caps.latest.revision: "19"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 5470b86096170410b88c6a8e8a596fe608d33cc7
ms.sourcegitcommit: ef1fa818beea435f58986af3379853dc28f5efd8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2017
---
# <a name="rename-a-database"></a>Cambiar el nombre de una base de datos
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] En este tema se describe cómo cambiar el nombre de una base de datos definida por el usuario en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. El nombre de la base de datos puede incluir cualquier carácter que se ajuste a las reglas para identificadores.  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Limitaciones y restricciones](#Restrictions)  
  
     [Seguridad](#Security)  
  
-   **Para cambiar el nombre de una base de datos, use:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Seguimiento:**  [Después de cambiar el nombre de una base de datos](#FollowUp)  

> [!NOTE]
> Para cambiar el nombre de una base de datos en Azure SQL Database, use la instrucción [ALTER DATABASE (Azure SQL Database)](../../t-sql/statements/alter-database-azure-sql-database.md). Para cambiar el nombre de una base de datos en Azure SQL Data Warehouse o en Almacenamiento de datos paralelos, utilice la instrucción [RENAME (Transact-SQL)](/t-sql/statements/rename-transact-sql).
  
##  <a name="BeforeYouBegin"></a> Antes de empezar  
  
###  <a name="Restrictions"></a> Limitaciones y restricciones  
  
-   No se puede cambiar el nombre de las bases de datos del sistema.  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 Requiere el permiso ALTER en la base de datos.  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
  
#### <a name="to-rename-a-database"></a>Para cambiar el nombre de una base de datos  
  
1.  En el **Explorador de objetos**, conéctese a una instancia del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]y, a continuación, expándala.  
  
2.  Asegúrese de que nadie usa la base de datos y luego [establezca la base de datos en modo de usuario único](../../relational-databases/databases/set-a-database-to-single-user-mode.md).  
  
3.  Expanda **Bases de datos**, haga clic con el botón derecho en la base de datos cuyo nombre quiere cambiar y luego haga clic en **Cambiar nombre**.  
  
4.  Escriba el nuevo nombre de la base de datos y haga clic en **Aceptar**.  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
  
#### <a name="to-rename-a-database"></a>Para cambiar el nombre de una base de datos  
  
1.  Conéctese con el [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**. Este ejemplo cambia el nombre de la base de datos `AdventureWorks2012` a `Northwind`.  
  
```tsql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
Modify Name = Northwind ;  
GO  
```  
  
###  <a name="TsqlExample"></a>   
##  <a name="FollowUp"></a> Seguimiento: Después de cambiar el nombre de una base de datos  
 Después de cambiar el nombre de cualquier base de datos, realice una copia de seguridad de la base de datos **maestra** .  
  
## <a name="see-also"></a>Vea también  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [Identificadores de base de datos](../../relational-databases/databases/database-identifiers.md)  
  
  
