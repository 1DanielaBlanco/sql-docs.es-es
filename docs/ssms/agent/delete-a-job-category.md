---
title: "Eliminar una categoría de trabajo | Microsoft Docs"
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
- SQL Server Agent jobs, categories
- deleting job category
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- removing job category
ms.assetid: 47a7640b-20b3-4639-ab37-b6fc73575e6c
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 044f52ffbf373622b820014862497361316afc3f
ms.contentlocale: es-es
ms.lasthandoff: 06/22/2017

---
# <a name="delete-a-job-category"></a>Eliminar una categoría de trabajo
En este tema se describe cómo eliminar una categoría de trabajo del Agente [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] en [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], [!INCLUDE[tsql](../../includes/tsql_md.md)] u Objetos de administración de SQL Server.  
  
Las categorías de trabajo le ayudan a organizar los trabajos para poder filtrarlos y agruparlos fácilmente. Por ejemplo, puede organizar todos los trabajos de copia de seguridad de las bases de datos en la categoría Mantenimiento de bases de datos.  
  
**En este tema**  
  
-   **Antes de empezar:**  
  
    [Limitaciones y restricciones](#Restrictions)  
  
    [Seguridad](#Security)  
  
-   **Para eliminar una categoría de trabajo, utilizando:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [objetos de administración de SQL Server](#SMO)  
  
## <a name="BeforeYouBegin"></a>Antes de comenzar  
  
### <a name="Restrictions"></a>Limitaciones y restricciones  
Al eliminar una categoría de trabajo definida por el usuario, el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] le solicita que vuelva a asignar los trabajos asignados a ella a otra categoría de trabajo. Solo puede eliminar categorías de trabajo definidas por el usuario.  
  
### <a name="Security"></a>Seguridad  
Para obtener información detallada, vea [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Usar SQL Server Management Studio  
  
#### <a name="to-delete-a-job-category"></a>Para eliminar una categoría de trabajo  
  
1.  En el **Explorador de objetos**, haga clic en el signo más para expandir el servidor en el que desea eliminar una categoría de trabajo.  
  
2.  Haga clic en el signo más para expandir **Agente SQL Server**.  
  
3.  Haga clic con el botón derecho en la carpeta **Trabajos** y seleccione **Administrar categorías de trabajos**.  
  
4.  En el cuadro de diálogo **Administrar categorías de trabajos***nombre_servidor* , seleccione la categoría de trabajo que desea eliminar.  
  
5.  Haga clic en **Eliminar**.  
  
6.  En el cuadro de diálogo **Categorías de trabajo** , haga clic en **Sí**.  
  
7.  En el cuadro de diálogo **Administrar categorías de trabajos***nombre_servidor* .  
  
## <a name="TSQL"></a>Usar Transact-SQL  
  
#### <a name="to-delete-a-job-category"></a>Para eliminar una categoría de trabajo  
  
1.  En el **Explorador de objetos**, conéctese a una instancia del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  En la barra de Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**.  
  
    ```  
    -- deletes the job category named AdminJobs.  
    USE msdb ;  
    GO   
    EXEC dbo.sp_delete_category  
        @name = N'AdminJobs',  
        @class = N'JOB' ;  
    GO  
    ```  
  
Para más información, consulte [sp_delete_category (Transact-SQL)](http://msdn.microsoft.com/en-us/63ea7d0d-a567-456e-a778-bee99e21d16c).  
  
## <a name="SMO"></a>Usar Objetos de administración de SQL Server  
**Para eliminar una categoría de trabajo**  
  
Llame a la clase **JobCategory** mediante un lenguaje de programación de su elección, como Visual Basic, Visual C# o PowerShell.  
  

