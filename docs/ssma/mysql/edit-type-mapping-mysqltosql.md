---
title: "Editar la asignación de tipo (MySQLToSQL) | Documentos de Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 184f7ab2-725f-491e-a15b-b889f2fb6a68
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ed31beae92c3453917a2fbcfd8ea1643c26a114c
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="edit-type-mapping-mysqltosql"></a>Editar la asignación de tipo (MySQLToSQL)
El **Editar asignación de tipo** cuadro de diálogo permite especificar cómo se asignan los tipos entre los objetos de base de datos de origen y de destino.  
  
Puede tener acceso a este cuadro de diálogo en varios lugares:  
  
-   Cuando se selecciona una base de datos de origen o un objeto de base de datos, el **Type Mapping** ficha aparece a la derecha del explorador de metadatos. Haga clic en **agregar** para agregar una nueva asignación de tipo, o haga clic en **editar** para cambiar una asignación de tipo existente.  
  
-   En el **herramientas** menú, seleccione **configuración del proyecto** o **configuración de proyecto predeterminada**. En el cuadro de diálogo que aparece, seleccione **asignación de tipo**. Haga clic en **agregar** para agregar una nueva asignación de tipo, o haga clic en **editar** para cambiar una asignación de tipo existente.  
  
-   Asignaciones de tipo específico de la tabla invalidación base de datos y las asignaciones de tipos de proyecto. Las asignaciones específicas de la base de datos invalidan las asignaciones de project.  
  
## <a name="options"></a>Opciones  
  
##### <a name="source-type"></a>Tipo de origen  
Seleccione el tipo de datos de origen se asignan a un tipo de datos de SQL Server.  
  
Si el tipo de datos es de longitud variable, los siguientes campos aparecerán en **Sourcetype**:  
  
##### <a name="from"></a>De  
Especifique la longitud mínima de esta asignación. Por ejemplo, para la **nchar** tipo de datos, puede especificar 10 para especificar que esta asignación es para un intervalo que comience en **nchar(10).**  
  
##### <a name="to"></a>A  
Especifique la longitud máxima de esta asignación. Por ejemplo, para la **nchar** tipo de datos, puede escribir 20 para especificar que esta asignación es para un intervalo finaliza **nchar (20).**  
  
##### <a name="target-type"></a>Tipo de destino  
Seleccione el tipo de datos de SQL Server al que está asignado el tipo de datos de origen. Cuando SSMA crea la tabla o en el servidor SQL Server, cambiará el tipo de datos de origen para este tipo de datos.  
  
Si el tipo de datos es de longitud variable, el siguiente campo aparecerá bajo **tipo de destino**:  
  
##### <a name="replace-with"></a>Reemplazar con  
Especifique la longitud de destino para esta asignación. Por ejemplo, para la **nvarchar** tipo de datos, puede escribir 20 para especificar que el tipo de datos de origen especificado debe asignarse a **nvarchar (20).**  
  

