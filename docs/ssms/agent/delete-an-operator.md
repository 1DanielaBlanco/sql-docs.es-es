---
title: Eliminar un operador | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent jobs, operators
- canceling operators
- removing operators
- deleting operators
- dropping operators
- jobs [SQL Server Agent], operators
- operators (users) [Database Engine], deleting with Management Studio
ms.assetid: 2b7b8627-082d-4189-8584-abd3a9b604cf
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e34da1cc7395a20132d808039834262d66c50887
ms.contentlocale: es-es
ms.lasthandoff: 06/22/2017

---
# <a name="delete-an-operator"></a>Delete an Operator
En este tema se describe cómo quitar un operado para que deje de recibir notificaciones de alerta del Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] en [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] o [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**En este tema**  
  
-   **Antes de empezar:**  
  
    [Limitaciones y restricciones](#Restrictions)  
  
    [Seguridad](#Security)  
  
-   **Para eliminar un operador, utilizando:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Antes de comenzar  
  
### <a name="Restrictions"></a>Limitaciones y restricciones  
Cuando se quita un operador, se quitan también todas las notificaciones asociadas con él.  
  
### <a name="Security"></a>Seguridad  
  
#### <a name="Permissions"></a>Permissions  
Los miembros del rol fijo de servidor **sysadmin** pueden eliminar operadores.  
  
## <a name="SSMSProcedure"></a>Usar SQL Server Management Studio  
  
#### <a name="to-delete-an-operator"></a>Para eliminar un operador  
  
1.  En el **Explorador de objetos**, haga clic en el signo más para expandir el servidor que contiene el operador que desea eliminar.  
  
2.  Haga clic en el signo más para expandir **Agente SQL Server**.  
  
3.  Haga clic en el signo más para expandir la carpeta **Operadores** .  
  
4.  Haga clic con el botón derecho en el operador que desea eliminar y seleccione **Eliminar**.  
  
5.  En el cuadro de diálogo **Eliminar objeto** , asegúrese de que está seleccionado el operador correcto y haga clic en **Aceptar**. Para que otro operador reciba las alertas y trabajos enviados al operador eliminado, active **Volver a asignar a** y seleccione un operador de la lista.  
  
## <a name="TsqlProcedure"></a>Usar Transact-SQL  
  
#### <a name="to-delete-an-operator"></a>Para eliminar un operador  
  
1.  En el **Explorador de objetos**, conéctese a una instancia del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  En la barra de Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**.  
  
    ```  
    -- deletes operator 'Test Operator' and reassigns all alerts and jobs
    --  sent to that operator to 'François Ajenstat'  
    USE msdb ;  
    GO  
  
    EXEC sp_delete_operator @name = 'Test Operator',  
        @reassign_to_operator = 'François Ajenstat';  
    GO  
    ```  
  
Para más información, consulte [sp_delete_operator (Transact-SQL)](http://msdn.microsoft.com/en-us/ff6c2c4b-e9fe-4d0c-bbc2-a2ddcc1acb95).  
  

