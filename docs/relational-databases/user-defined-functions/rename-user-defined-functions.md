---
title: Cambio de nombre de las funciones definidas por el usuario | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-udf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2695a5c-9cc5-4b18-8771-53027ca9a9af
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6af95b4d0b4bc3b8e652fd40fa1427cd156c1514
ms.lasthandoff: 04/11/2017

---
# <a name="rename-user-defined-functions"></a>Cambiar el nombre de las funciones definidas por el usuario
  Puede cambiar el nombre de las funciones definidas por el usuario en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **En este tema**  
  
-   **Antes de empezar:**  
  
     [Limitaciones y restricciones](#Restrictions)  
  
     [Seguridad](#Security)  
  
-   **Para cambiar el nombre de las funciones definidas por el usuario, con:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de comenzar  
  
###  <a name="Restrictions"></a> Limitaciones y restricciones  
  
-   Los nombres de las funciones deben ajustarse a las reglas de los [identificadores](../../relational-databases/databases/database-identifiers.md).  
  
-   Al cambiar el nombre de una función definida por el usuario no se cambiará el nombre del objeto correspondiente en la columna de definición de la vista de catálogo **sys.sql_modules** . Por tanto, se recomienda no cambiar este tipo de objeto. En su lugar, quite el procedimiento almacenado y vuelva a crearlo con su nuevo nombre.  
  
-   El hecho de cambiar el nombre o la definición de una función definida por el usuario puede provocar errores en los objetos dependientes si no se actualizan con arreglo a los cambios realizados en la función.  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 Para quitar la función, se requiere el permiso ALTER en el esquema al que pertenece la función o un permiso CONTROL en la función. Para volver a crear la función, se requiere el permiso CREATE FUNCTION en la base de datos y el permiso ALTER en el esquema en el que se va a crear la función.  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
  
#### <a name="to-rename-user-defined-functions"></a>Para cambiar el nombre de las funciones definidas por el usuario  
  
1.  En el **Explorador de objetos**, haga clic en el signo más situado junto a la base de datos que contiene la función a la que desea cambiar el nombre y  
  
2.  Haga clic en el signo más junto a la carpeta **Programación** .  
  
3.  Haga clic en el signo más junto a la carpeta que contenga la función cuyo nombre desea cambiar:  
  
    -   Table-valued Function  
  
    -   Función con valor escalar  
  
    -   Función de agregado  
  
4.  Haga clic con el botón derecho en la función cuyo nombre quiere cambiar y seleccione **Cambiar nombre**.  
  
5.  Escriba el nuevo nombre de la función.  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
 **Para cambiar el nombre de las funciones definidas por el usuario**  
  
 Esta tarea no se puede realizar mediante instrucciones Transact-SQL. Para cambiar una función definida por el usuario mediante Transact-SQL, debe eliminar la función existente y volver a crearla con el nuevo nombre. Asegúrese de que todo el código y las aplicaciones que usaban el nombre antiguo de la función usan el nuevo nombre.  
  
 Para obtener más información, vea [CREATE FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-function-transact-sql.md) y [DROP FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-function-transact-sql.md).  
  
## <a name="see-also"></a>Vea también  
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)   
 [Ver funciones definidas por el usuario](../../relational-databases/user-defined-functions/view-user-defined-functions.md)  
  
  
