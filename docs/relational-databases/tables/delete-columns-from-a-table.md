---
title: "Eliminación de columnas desde una tabla (motor de base de datos) | Microsoft Docs"
ms.custom: 
ms.date: 04/11/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [SQL Server], deleting
- removing columns
- deleting columns
- dropping columns
ms.assetid: 0d8f6e4f-bc71-4fa3-8615-74249c8e072d
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: HT
ms.sourcegitcommit: 621185759462020bca20985c3133c93814a1f333
ms.openlocfilehash: ef0c4b8b66af5dfc46c836fc8c18734609b1301a
ms.contentlocale: es-es
ms.lasthandoff: 07/31/2017

---
# <a name="delete-columns-from-a-table"></a>Eliminar columnas de una tabla
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  En este tema se describe cómo eliminar columnas de tabla en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!CAUTION]  
>  Cuando se elimina una columna de una tabla, dicha columna y todos los datos que contiene se eliminan de la base de datos. No se puede deshacer esta acción.  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Limitaciones y restricciones](#Restrictions)  
  
     [Seguridad](#Security)  
  
-   **Para eliminar una columna de una tabla con:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Restrictions"></a> Limitaciones y restricciones  
 No puede eliminar una columna que tenga una restricción CHECK. Primero debe eliminar la restricción.  
  
 No puede eliminar una columna que tiene restricciones PRIMARY KEY o FOREIGN KEY u otras dependencias excepto si usa el Diseñador de tablas. Al utilizar el Explorador de objetos o [!INCLUDE[tsql](../../includes/tsql-md.md)], primero debe quitar todas las dependencias de la columna.  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 Requiere el permiso ALTER en la tabla.  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
  
#### <a name="to-delete-columns-by-using-object-explorer"></a>Para eliminar columnas mediante el Explorador de objetos  
  
1.  En el **Explorador de objetos**, conéctese a una instancia del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En el **Explorador de objetos**, busque la tabla de la que quiere eliminar columnas y expanda los nombres de esas columnas para exponerlas. 

3.  Haga clic con el botón derecho en la columna que quiera eliminar y, después, elija **Eliminar**.  
  
3.  En el cuadro de diálogo **Eliminar objeto** , haga clic en **Aceptar**.  
  
 Si la columna contiene restricciones u otras dependencias, aparecerá un mensaje de error en el cuadro de diálogo **Eliminar objeto** . Resuelva el error eliminando las restricciones a las que hace referencia.  
  
#### <a name="to-delete-columns-by-using-table-designer"></a>Para eliminar columnas mediante el Diseñador de tablas  
  
1.  En el **Explorador de objetos**, haga clic con el botón derecho en la tabla de la que quiere eliminar columnas y elija **Diseño**.  
  
2.  Haga clic con el botón derecho en la columna que quiera eliminar y elija **Eliminar columna** en el menú contextual.  
  
3.  Si la columna participa en una relación (FOREIGN KEY o PRIMARY KEY), un cuadro de mensaje le pedirá que confirme la eliminación de las columnas seleccionadas y sus relaciones. Elija **Sí**.  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
  
#### <a name="to-delete-columns"></a>Para eliminar columnas  
  
1.  En el **Explorador de objetos**, conéctese a una instancia del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra de Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE dbo.doc_exb DROP COLUMN column_b ;  
    ```  
  
 Si la columna contiene restricciones u otras dependencias, se devolverá un mensaje de error. Resuelva el error eliminando las restricciones a las que hace referencia.  
  
 Para obtener otros ejemplos, vea [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md).  
  
##  <a name="FollowUp"></a>  

