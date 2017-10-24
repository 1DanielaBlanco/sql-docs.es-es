---
title: Crear una base de datos (Tutorial) | Documentos de Microsoft
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
- tutorial creating a database
ms.assetid: e1e2c83f-dfad-4bb8-aa7a-09d3f69517ae
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6628dcf0ab38db441de9bd9324e69993e5759c38
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-1-1---creating-a-database"></a>Lección 1-1-crear una base de datos
Como muchas instrucciones de [!INCLUDE[tsql](../includes/tsql-md.md)] , la instrucción CREATE DATABASE tiene un parámetro requerido: el nombre de la base de datos. CREATE DATABASE también tiene muchos parámetros opcionales, como la ubicación de disco donde se desean colocar los archivos de la base de datos. Si se ejecuta CREATE DATABASE sin los parámetros opcionales, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] usa los valores predeterminados para muchos de estos parámetros. Este tutorial usa algunos de los parámetros de sintaxis opcionales.  
  
### <a name="to-create-a-database"></a>Para crear una base de datos  
  
1.  En una ventana del Editor de consultas, escriba el código siguiente, pero no lo ejecute:  
  
    ```  
    CREATE DATABASE TestData  
    GO  
    ```  
  
2.  Use el puntero para seleccionar las palabras `CREATE DATABASE`y, a continuación, presione **F1**. Debe abrirse el tema CREATE DATABASE de los Libros en pantalla de SQL Server. Puede usar esta técnica para encontrar la sintaxis completa de CREATE DATABASE y de otras instrucciones que se usan en este tutorial.  
  
3.  En el Editor de consultas, presione **F5** para ejecutar la instrucción y crear una base de datos con el nombre `TestData`.  
  
Al crear una base de datos, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] realiza una copia de la base de datos **model** y cambia el nombre de la copia por el nombre de la base de datos. Esta operación solo debería tardar algunos segundos, a menos que especifique un tamaño inicial grande de la base de datos como un parámetro opcional.  
  
> [!NOTE]  
> La palabra clave GO separa las instrucciones cuando se envían varias instrucciones en un solo lote. GO es opcional cuando el lote solo contiene una instrucción.  
  
## <a name="next-task-in-lesson"></a>Siguiente tarea de la lección  
[Crear una tabla &#40;Tutorial&#41;](../t-sql/lesson-1-2-creating-a-table.md)  
  
## <a name="see-also"></a>Vea también  
[CREATE DATABASE &#40;Transact-SQL de SQL Server&#41;](../t-sql/statements/create-database-sql-server-transact-sql.md)  
  
  
  

