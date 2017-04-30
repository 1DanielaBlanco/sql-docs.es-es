---
title: Generar proyectos de bases de datos mediante SQL Server Management Studio | Microsoft Docs
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
- scripts [SQL Server], database projects
- database projects [SQL Server]
- projects [SQL Server Management Studio], about projects
- projects [SQL Server Management Studio]
ms.assetid: c2e80045-894d-44cf-b65c-e547ed738947
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: a3487f9048571511460bc22b5c0b605592ba74f5
ms.lasthandoff: 04/11/2017

---
# <a name="build-database-projects-by-using-sql-server-management-studio"></a>Generar proyectos de bases de datos mediante SQL Server Management Studio
Un proyecto de scripts de base de datos es un conjunto organizado de scripts, información de conexión y plantillas asociado a una base de datos o a parte de ella. [!INCLUDE[msCoName](../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] proporciona [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] para administrar y diseñar bases de datos [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] en el contexto de un proyecto de script. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] incluye diseñadores, editores, guías y asistentes para ayudar a los usuarios a desarrollar, implementar y mantener bases de datos.  
  
## <a name="sql-server-management-studio"></a>SQL Server Management Studio  
[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] es un conjunto de herramientas administrativas que permite administrar los componentes que pertenecen a [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)]. Este entorno integrado permite a los usuarios realizar varias tareas, como realizar copias de seguridad de los datos, editar consultas y automatizar funciones comunes en una misma interfaz.  
  
[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] incluye las siguientes herramientas:  
  
-   El Editor de código es un editor de script completo que sirve para escribir y modificar scripts. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] proporciona cuatro versiones del Editor de código: el Editor de consultas del [!INCLUDE[ssDE](../includes/ssde_md.md)] para scripts [!INCLUDE[tsql](../includes/tsql_md.md)] , el Editor de consultas de MDX, el Editor de consultas de MDX y el Editor de consultas de XML/A.  
  
-   El Explorador de objetos sirve para buscar, modificar e incluir en scripts objetos que pertenecen a instancias de [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)]o ejecutarlos.  
  
-   El Explorador de plantillas sirve para buscar plantillas y crear scripts para ellas.  
  
-   El Explorador de soluciones sirve para organizar y almacenar scripts relacionados como partes de un proyecto.  
  
-   La Ventana Propiedades sirve para mostrar las propiedades actuales de los objetos seleccionados.  
  
[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] permite desarrollar procesos de trabajo de manera eficaz al proporcionar:  
  
-   Acceso sin conexión. Puede escribir y modificar scripts sin conectarse a una instancia de [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)].  
  
-   Creación de scripts desde cualquier cuadro de diálogo. Puede crear un script desde cualquier cuadro de diálogo para que pueda leer, modificar, almacenar y reutilizar los scripts después de crearlos.  
  
-   Cuadros de diálogo no modales. Al obtener acceso a un cuadro de diálogo de interfaz de usuario, puede examinar otros recursos en [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull_md.md)] sin cerrar el cuadro de diálogo.  
  
## <a name="solutions-and-script-projects"></a>Soluciones y proyectos de scripts  
El Explorador de soluciones es una utilidad que sirve para almacenar y volver a abrir soluciones de bases de datos. Las soluciones organizan proyectos de scripts y archivos relacionados. Los proyectos de script almacenan archivos de scripts de [!INCLUDE[ssNoVersion](../includes/ssnoversion_md.md)] , plantillas SQL, información de conexión y otros archivos varios. Cuando se guarda un script en un proyecto de scripts, los usuarios pueden:  
  
-   Mantener un control de versiones de los scripts.  
  
-   Almacenar opciones de resultados con un script.  
  
-   Organizar los scripts relacionados en un solo proyecto de script.  
  
-   Guardar información de conexión con scripts.  
  
El Explorador de soluciones es una herramienta para los programadores que crean y reutilizan scripts relacionados con el mismo proyecto. Si se requiere realizar una tarea similar posteriormente, puede utilizar el grupo de scripts que se almacenó en un proyecto. Si creó aplicaciones mediante [!INCLUDE[msCoName](../includes/msconame_md.md)] [!INCLUDE[vsprvs](../includes/vsprvs_md.md)], el Explorador de soluciones le resultará muy familiar.  
  
Una solución consta de uno o más proyectos de script. Un proyecto está formado por uno o más scripts o conexiones. Un proyecto también puede incluir archivos que no sean scripts.  
  
## <a name="see-also"></a>Vea también  
[Usar SQL Server Management Studio](../ssms/use-sql-server-management-studio.md)  
[Escribir, analizar y editar consultas con SQL Server Management Studio](http://msdn.microsoft.com/en-us/062051e4-4b77-4969-98ae-d2547c24ce3e)  
[Soluciones &amp;#40;SQL Server Management Studio&amp;#41;](../ssms/solution/solutions-sql-server-management-studio.md)  
  

