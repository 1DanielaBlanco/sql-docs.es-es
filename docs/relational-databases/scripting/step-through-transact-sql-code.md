---
title: "Avanzar paso a paso por el c&#243;digo Transact-SQL | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurador de Transact-SQL, código de depuración"
  - "depurador de Transact-SQL, paso a paso por procedimientos"
  - "depurador de Transact-SQL, paso a paso para salir"
  - "depurador de Transact-SQL, paso a paso por instrucciones"
ms.assetid: e09079b8-c4c9-42b4-821b-4ce81a98a086
caps.latest.revision: 19
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 18
---
# Avanzar paso a paso por el c&#243;digo Transact-SQL
  El depurador de [!INCLUDE[tsql](../../includes/tsql-md.md)] permite controlar las instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)] que se ejecutan en una ventana del Editor de consultas de [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Puede detener el depurador en instrucciones individuales y, a continuación, ver el estado de los elementos de código en ese punto.  
  
## Puntos de interrupción  
 Un punto de interrupción indica al depurador que detenga la ejecución en una instrucción [!INCLUDE[tsql](../../includes/tsql-md.md)] específica. Para obtener más información sobre los puntos de interrupción, vea Utilizar puntos de interrupción de Transact-SQL.  
  
## Controlar la ejecución de instrucciones  
 En el depurador de [!INCLUDE[tsql](../../includes/tsql-md.md)] , puede especificar las siguientes opciones para su ejecución desde la instrucción actual del código [!INCLUDE[tsql](../../includes/tsql-md.md)] :  
  
-   Ejecutar un proceso hasta el siguiente punto de interrupción.  
  
-   Ir a la siguiente instrucción.  
  
     Si la siguiente instrucción invoca un procedimiento almacenado, función o desencadenador de [!INCLUDE[tsql](../../includes/tsql-md.md)] , el depurador muestra una nueva ventana del Editor de consultas que contiene el código del módulo. La ventana está en el modo de depuración y la ejecución se detiene en la primera instrucción del módulo. Después puede desplazarse por el código del módulo, por ejemplo, estableciendo puntos de interrupción o recorriendo el código.  
  
-   Paso a paso por la siguiente instrucción.  
  
     Se ejecuta la siguiente instrucción. Sin embargo, si la instrucción invoca un procedimiento almacenado, una función o un desencadenador, el código del módulo se ejecuta hasta que termine y los resultados se devuelven al código de llamada. Si está seguro de que no hay errores en un procedimiento almacenado, puede omitirlo. La ejecución se detiene en la instrucción que sigue a la llamada al procedimiento almacenado, a la función o al desencadenador.  
  
-   Salir de un procedimiento almacenado, función o desencadenador.  
  
     La ejecución se detiene en la instrucción que sigue a la llamada al procedimiento almacenado, a la función o al desencadenador.  
  
-   Ejecutar el proceso desde la ubicación actual hasta la ubicación actual del puntero e ignorar todos los puntos de interrupción.  
  
 La tabla siguiente muestra las distintas formas en las que puede controlar la ejecución de las instrucciones del depurador de [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
|Acción|Realizar acción:|  
|------------|---------------------|  
|Ejecutar todas las instrucciones desde la instrucción actual hasta el siguiente punto de interrupción|Haga clic en **Continuar** en el menú **Depurar** .<br /><br /> Haga clic en el botón **Continuar** en la barra de herramientas **Depurar** .|  
|Ir a la siguiente instrucción o módulo|Haga clic en **Paso a paso por instrucciones** en el menú **Depurar** .<br /><br /> Haga clic en el botón **Paso a paso por instrucciones** en la barra de herramientas **Depurar** .<br /><br /> Presione F11.|  
|Paso a paso por la siguiente instrucción o módulo|Haga clic en **Paso a paso por procedimientos** en el menú **Depurar** .<br /><br /> Haga clic en el botón **Paso a paso por procedimientos** en la barra de herramientas **Depurar** .<br /><br /> Presione F10.|  
|Salir de un módulo|Haga clic en **Paso a paso para salir** en el menú **Depurar** .<br /><br /> Haga clic en el botón **Paso a paso para salir** en la barra de herramientas **Depuración** .<br /><br /> Presione MAYÚS+F11.|  
|Ejecutar un proceso hasta la ubicación del cursor actual|Haga clic con el botón derecho en la ventana del Editor de consultas y, después, haga clic en **Ejecutar hasta el cursor**.<br /><br /> Presione CTRL+F10.|  
  
## Vea también  
 [Ver información del depurador de Transact-SQL](../../relational-databases/scripting/transact-sql-debugger-information.md)  
  
  