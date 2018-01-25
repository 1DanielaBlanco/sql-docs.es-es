---
title: Modificar los servidores de destino para un trabajo | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying target servers
- SQL Server Agent jobs, target servers
- target servers [SQL Server], modifying
ms.assetid: 9dbe24f2-acec-4aa2-920c-e8e96efa18e4
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 12c25d2c5583612253fba3320cd632cba86e8950
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="modify-the-target-servers-for-a-job"></a>Modify the Target Servers for a Job
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] En este tema se describe cómo cambiar los servidores de destino para trabajos del Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] en [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] o [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**En este tema**  
  
-   **Antes de empezar:**  
  
    [Seguridad](#Security)  
  
-   **Para modificar los servidores de destino para un trabajo, usando:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Antes de empezar  
  
### <a name="Security"></a>Seguridad  
  
#### <a name="Permissions"></a>Permissions  
De forma predeterminada, los miembros del rol fijo de servidor sysadmin pueden ejecutar este procedimiento almacenado. Al resto de usuarios se les debe conceder uno de los siguientes roles fijos de base de datos del Agente SQL Server en la base de datos msdb:  
  
1.  **SQLAgentUserRole**  
  
2.  **SQLAgentReaderRole**  
  
3.  SQLAgentOperatorRole  
  
## <a name="SSMSProcedure"></a>Usar SQL Server Management Studio  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a>Para modificar los servidores de destino para un trabajo  
  
1.  En el **Explorador de objetos** , conéctese a una instancia de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]y, después, expándala.  
  
2.  Expanda **Agente SQL Server**, expanda **Trabajos**, haga clic con el botón derecho en un trabajo y, luego, haga clic en **Propiedades**.  
  
3.  En el cuadro de diálogo **Propiedades del trabajo** , seleccione la página **Destinos**y haga clic en **Destino en servidor local**o **Destino en varios servidores**.  
  
    Si elige **Destino en varios servidores**, designe los servidores que serán destinos para el trabajo activando la casilla situada a la izquierda del nombre del servidor. Compruebe que las casillas de los servidores que no serán destinos del trabajo están desactivadas.  
  
## <a name="TsqlProcedure"></a>Usar Transact-SQL  
  
#### <a name="to-modify-the-target-servers-for-a-job"></a>Para modificar los servidores de destino para un trabajo  
  
1.  Conéctese con el [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**. En este ejemplo se asigna el trabajo multiservidor Weekly Sales Backups al servidor SEATTLE2.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_jobserver  
    @job_name = N'Weekly Sales Backups',   
    @server_name = N'SEATTLE2' ;   
GO  
```  
  
Para más información, consulte [sp_add_jobserver (Transact-SQL)](http://msdn.microsoft.com/en-us/485252cc-0081-490a-9bd1-cbbd68eea286).  
  
## <a name="see-also"></a>Ver también  
[Administración automatizada en una empresa](../../ssms/agent/automated-administration-across-an-enterprise.md)  
  
