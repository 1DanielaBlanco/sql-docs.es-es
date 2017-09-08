---
title: Eliminar objetos de base de datos | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- deleting database objects
ms.assetid: dbb94fdf-c85b-477b-8e84-f830d259bade
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7bcd4f3254cfd6b648411ae6fb9c364fa7017913
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-3-1---deleting-database-objects"></a>Lección 3-1: eliminar objetos de base de datos
Para quitar todas los seguimientos de este tutorial, podría eliminar únicamente la base de datos. No obstante, en este tema, recorrerá los pasos para revertir cada una de las acciones llevadas a cabo en el tutorial.  
  
### <a name="removing-permissions-and-objects"></a>Quitar permisos y objetos  
  
1.  Antes de eliminar objetos, asegúrese de que está en la base de datos correcta:  
  
    ```  
    USE TestData;  
    GO  
    ```  
  
2.  Use la instrucción `REVOKE` para quitar el permiso de ejecución para `Mary` en el procedimiento almacenado:  
  
    ```  
    REVOKE EXECUTE ON pr_Names FROM Mary;  
    GO  
  
    ```  
  
3.  Use la instrucción `DROP` para quitar el permiso de `Mary` para tener acceso a la base de datos `TestData` :  
  
    ```  
    DROP USER Mary;  
    GO  
  
    ```  
  
4.  Use la instrucción `DROP` para quitar el permiso de `Mary` para tener acceso a esta instancia de [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]:  
  
    ```  
    DROP LOGIN [<computer_name>\Mary];  
    GO  
  
    ```  
  
5.  Use la instrucción `DROP` para quitar el procedimiento almacenado `pr_Names`:  
  
    ```  
    DROP PROC pr_Names;  
    GO  
  
    ```  
  
6.  Use la instrucción `DROP` para quitar la vista `vw_Names`:  
  
    ```  
    DROP View vw_Names;  
    GO  
  
    ```  
  
7.  Use la instrucción `DELETE` para quitar todas las filas de la tabla `Products` :  
  
    ```  
    DELETE FROM Products;  
    GO  
  
    ```  
  
8.  Use la instrucción `DROP` para quitar la tabla `Products` :  
  
    ```  
    DROP Table Products;  
    GO  
  
    ```  
  
9. No puede quitar la base de datos `TestData` mientras esté en la base de datos; por tanto, cambie primero el contexto a otra base de datos y, a continuación, use la instrucción `DROP` para quitar la base de datos `TestData` :  
  
    ```  
    USE MASTER;  
    GO  
    DROP DATABASE TestData;  
    GO  
  
    ```  
  
Esto finaliza el tutorial de escritura de instrucciones [!INCLUDE[tsql](../includes/tsql-md.md)] . Recuerde que este tutorial es una introducción breve y en él no se describen todas las opciones de las instrucciones que se usan. El diseño y la creación de una estructura de base de datos eficaz y la configuración del acceso seguro a los datos requiere una base de datos más compleja que la que se muestra en este tutorial.  
  
## <a name="return-to-sql-server-tools-portal"></a>Volver al portal de las herramientas de SQL Server  
[Tutorial: Escribir instrucciones Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md)  
  
## <a name="see-also"></a>Vea también  
[REVOKE &#40;Transact-SQL&#41;](../t-sql/statements/revoke-transact-sql.md)  
[DROP USER &#40;Transact-SQL&#41;](../t-sql/statements/drop-user-transact-sql.md)  
[DROP LOGIN &#40;Transact-SQL&#41;](../t-sql/statements/drop-login-transact-sql.md)  
[DROP PROCEDURE &#40;Transact-SQL&#41;](../t-sql/statements/drop-procedure-transact-sql.md)  
[DROP VIEW &#40;Transact-SQL&#41;](../t-sql/statements/drop-view-transact-sql.md)  
[DELETE &#40;Transact-SQL&#41;](../t-sql/statements/delete-transact-sql.md)  
[DROP TABLE &#40;Transact-SQL&#41;](../t-sql/statements/drop-table-transact-sql.md)  
[DROP DATABASE &#40;Transact-SQL&#41;](../t-sql/statements/drop-database-transact-sql.md)  
  
  
  

