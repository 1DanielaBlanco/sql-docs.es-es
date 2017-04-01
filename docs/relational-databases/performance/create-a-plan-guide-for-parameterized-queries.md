---
title: "Crear una gu&#237;a de plan para consultas parametrizadas | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-plan-guides"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "consultas con parámetros, guías de plan para"
  - "guías de plan [SQL Server], consultas con parámetros"
ms.assetid: b532ae16-66e7-4641-9bc8-b0d805853477
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# Crear una gu&#237;a de plan para consultas parametrizadas
  Una guía de plan TEMPLATE compara consultas independientes que se parametrizan en un formulario especificado.  
  
 En el ejemplo siguiente se crea una guía de plan que coincida con cualquier consulta que se parametrice de una forma específica, e indica a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que fuerce la parametrización de la consulta. Las dos consultas siguientes son equivalentes desde el punto de vista sintáctico, pero se diferencian solo en los valores literales de las constantes.  
  
```  
SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
    ON h.SalesOrderID = d.SalesOrderID  
WHERE h.SalesOrderID = 45639;  
  
SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
    ON h.SalesOrderID = d.SalesOrderID  
WHERE h.SalesOrderID = 45640;  
```  
  
 Ésta es una guía de plan creada en la consulta con parámetros:  
  
```  
EXEC sp_create_plan_guide   
    @name = N'TemplateGuide1',  
    @stmt = N'SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
              INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
                  ON h.SalesOrderID = d.SalesOrderID  
              WHERE h.SalesOrderID = @0',  
    @type = N'TEMPLATE',  
    @module_or_batch = NULL,  
    @params = N'@0 int',  
    @hints = N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
 En el ejemplo anterior, el valor del parámetro `@stmt` representa la forma de la consulta con parámetros. La única manera confiable de obtener este valor para usarlo en sp_create_plan_guide es recurrir al procedimiento almacenado del sistema [sp_get_query_template](../../relational-databases/system-stored-procedures/sp-get-query-template-transact-sql.md). El script siguiente se puede utilizar para obtener la consulta con parámetros y, después crear una guía de plan basada en ella.  
  
```  
DECLARE @stmt nvarchar(max);  
DECLARE @params nvarchar(max);  
EXEC sp_get_query_template   
    N'SELECT * FROM AdventureWorks2012.Sales.SalesOrderHeader AS h  
      INNER JOIN AdventureWorks2012.Sales.SalesOrderDetail AS d   
          ON h.SalesOrderID = d.SalesOrderID  
      WHERE h.SalesOrderID = 45639;',  
    @stmt OUTPUT,   
    @params OUTPUT  
EXEC sp_create_plan_guide N'TemplateGuide1',   
    @stmt,   
    N'TEMPLATE',   
    NULL,   
    @params,   
    N'OPTION(PARAMETERIZATION FORCED)';  
```  
  
> [!IMPORTANT]  
>  El valor de los literales de constante del parámetro `@stmt` pasado a `sp_get_query_template` podría afectar al tipo de datos elegido para el parámetro que reemplaza al valor literal. Esto afectaría a la correspondencia de la guía de plan. Puede que tenga que crear más de una guía de plan para abarcar los distintos intervalos de valores de parámetros.  
  
 También puede utilizar las guías de plan TEMPLATE junto con guías de plan SQL. Por ejemplo, puede crear una guía de plan TEMPLATE para asegurarse de que se parametriza una clase de consultas. A continuación, puede crear una guía de plan SQL en el formulario parametrizado de esa consulta.  
  
  