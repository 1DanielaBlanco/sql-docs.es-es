---
title: "Configuración (base de datos de SQL Azure) del proyecto (SybaseToSQL) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 57002374-0d4d-43c1-b4e9-cbec02355a9c
caps.latest.revision: "4"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c6d39a4ceb167746ffe1f47528ac8e042f45715a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="project-settings-azure-sql-db--sybasetosql"></a>Configuración (base de datos de SQL Azure) del proyecto (SybaseToSQL)
La configuración del proyecto de base de datos de SQL Azure le permite configurar el sufijo de la base de datos de base de datos de SQL Azure para agregar en el cuadro de diálogo de conexión y también permite implementar el mecanismo de latidos de conexión de base de datos de SQL Azure.  
  
El panel de la base de datos de SQL Azure está disponible en la **configuración del proyecto** y **configuración de proyecto predeterminada** cuadros de diálogo.  
  
-   Utilice el cuadro de diálogo de configuración del proyecto para establecer las opciones de configuración para el proyecto actual. Para acceder a la configuración de la base de datos de SQL Azure, en la **herramientas** menú, seleccione **configuración del proyecto**, haga clic en **General** en la parte inferior del panel izquierdo y, a continuación, seleccione **base de datos de SQL Azure**.  
  
-   Utilice el cuadro de diálogo de configuración de proyecto predeterminada para establecer las opciones de configuración para todos los proyectos. Para acceder a la configuración de la base de datos de SQL Azure, en la **herramientas** menú, seleccione **DefaultProject configuración**, haga clic en **General** en la parte inferior del panel izquierdo y, a continuación, seleccione **base de datos de SQL Azure**.  
  
## <a name="connectivity"></a>Conectividad  
**Intervalo de latidos**  
  
Especifica un intervalo de tiempo que se usará para el mecanismo de latidos para mantener activa en la conexión de base de datos de SQL de Azure ' minutos: formato de segundo.  
  
**Valor predeterminado**:' 4:45 '  
  
El valor debe especificarse en estoy: formato de ss (por ejemplo, ' 4:45 ' o ' 0:50 ').  
  
**Sufijo de servidor de base de datos de SQL Azure**  
  
Especifica un sufijo de servidor de base de datos de SQL Azure  
  
**Valor predeterminado**: 'database.windows.net'.  
  
