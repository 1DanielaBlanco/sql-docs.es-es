---
title: "Consulta de los datos de una tabla temporal con control de versiones del sistema | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/28/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2d358c2e-ebd8-4eb3-9bff-cfa598a39125
caps.latest.revision: 7
author: "CarlRabeler"
ms.author: "carlrab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Consulta de los datos de una tabla temporal con control de versiones del sistema
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Cuando quiera obtener el último estado de datos (actual) de una tabla temporal, puede consultarlo de la misma manera que lo haría en una tabla no temporal. Si no se ocultan las columnas PERIOD, sus valores se mostrarán en una consulta SELECT \*. Si especificó las columnas **PERIOD** como ocultas, sus valores no se mostrarán en una consulta SELECT \*. Cuando las columnas de **PERIOD** están ocultas, haga referencia a las columnas de **PERIOD** específicamente en la cláusula SELECT para devolver los valores de estas columnas.  
  
 Para realizar cualquier tipo de análisis basado en tiempo, use la nueva cláusula **FOR SYSTEM_TIME** con cuatro subcláusulas temporales específicas para consultar datos en las tablas actuales y de historial. Para obtener más información sobre estas cláusulas, vea [Tablas temporales](../../relational-databases/tables/temporal-tables.md) y [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md).  
  
-   AS OF <date_time>  
  
-   FROM <start_date_time> TO <end_date_time>  
  
-   BETWEEN <start_date_time> AND <end_date_time>  
  
-   CONTAINED IN (<start_date_time> , <end_date_time>)  
  
-   ALL  
  
 **FOR SYSTEM_TIME** puede especificarse de forma independiente para cada tabla de una consulta. Puede usarse dentro de expresiones comunes de tabla, de funciones con valores de tabla y de procedimientos almacenados.  
  
## Consulta de una hora específica con la subcláusula AS OF  
 Use la subcláusula **AS OF** cuando necesite reconstruir el estado de datos a como era en un momento concreto del pasado.  Puede reconstruir los datos con la precisión del tipo datetime2 que se especificó en las definiciones de la columna **PERIOD** .    
La subcláusula **AS OF** puede usarse con literales constantes o con variables, lo que permite especificar de forma dinámica una condición temporal. Los valores proporcionados se interpretan como hora UTC.  
  
 Este primer ejemplo devuelve el estado de la tabla dbo.Department en una fecha específica del pasado.  
  
```  
/*State of entire table AS OF specific date in the past*/   
SELECT [DeptID], [DeptName], [SysStartTime],[SysEndTime]   
FROM [dbo].[Department]   
FOR SYSTEM_TIME AS OF '2015-09-01 T10:00:00.7230011' ;  
  
```  
  
 Este segundo ejemplo compara los valores entre dos momentos dados de un subconjunto de filas.  
  
```  
DECLARE @ADayAgo datetime2   
SET @ADayAgo = DATEADD (day, -1, sysutcdatetime())   
/*Comparison between two points in time for subset of rows*/   
SELECT D_1_Ago.[DeptID], D.[DeptID],   
D_1_Ago.[DeptName], D.[DeptName],   
D_1_Ago.[SysStartTime], D.[SysStartTime],   
D_1_Ago.[SysEndTime], D.[SysEndTime]   
FROM [dbo].[Department] FOR SYSTEM_TIME AS OF @ADayAgo AS D_1_Ago   
JOIN [Department] AS D ON  D_1_Ago.[DeptID] = [D].[DeptID]    
AND D_1_Ago.[DeptID] BETWEEN 1 and 5 ;  
```  
  
### Usar vistas con la subcláusula AS OF en consultas temporales  
 Usar vistas es muy útil en escenarios en los que se requiere un análisis complejo de un momento dado.   
Un ejemplo común es generar un informe empresarial hoy con los valores del mes anterior.   
Normalmente, los clientes tienen un modelo normalizado de bases de datos que incluye muchas tablas con relaciones de clave externa. Responder a la pregunta de qué aspecto tienen los datos del modelo normalizado en un momento del pasado puede ser muy difícil, ya que todas las tablas cambian de forma independiente, a su ritmo.   
En este caso, la mejor opción es crear una vista y aplicar la subcláusula **AS OF** a la vista completa. El empleo de este enfoque permite desacoplar el modelado de la capa de acceso a datos desde un análisis de un momento dado, ya que SQL Server aplicará la cláusula **AS OF** de forma transparente a todas las tablas temporales que participen en la definición de la vista. Además, puede combinar tablas temporales y no temporales en la misma vista y **AS OF** se aplicará solo a las temporales. Si la vista no hace referencia al menos a una tabla temporal, al aplicarle las cláusulas de consulta temporal se producirá un error.  
  
```  
/* Create view that joins three temporal tables: Department, CompanyLocation, LocationDepartments */   
CREATE VIEW [dbo].[vw_GetOrgChart]   
AS   
SELECT   
     [CompanyLocation].LocID  
   , [CompanyLocation].LocName  
   , [CompanyLocation].City  
   , [Department].DeptID  
   , [Department].DeptName    
FROM [dbo].[CompanyLocation]   
LEFT JOIN [dbo].[LocationDepartments]    
   ON [CompanyLocation].LocID = LocationDepartments.LocID   
LEFT JOIN [dbo].[Department]    
   ON LocationDepartments.DeptID = [Department].DeptID ;  
GO   
/* Querying view AS OF */   
SELECT * FROM [vw_GetOrgChart]   
FOR SYSTEM_TIME AS OF '2015-09-01 T10:00:00.7230011' ;  
  
```  
  
## Consulta para realizar cambios en filas específicas a lo largo del tiempo  
 Las subcláusulas temporales **FROM...TO**, **BETWEEN...AND** y **CONTAINED IN** son útiles cuando se quiere realizar una auditoría de datos, es decir, cuando es necesario obtener todos los cambios históricos de una fila específica de la tabla actual.   
Las dos primeras subcláusulas devuelven versiones de fila que se superponen en un periodo específico (es decir, aquellas que empezaron antes del periodo dado y terminaron después de este), mientras que CONTAINED IN devuelve solo las que existieron dentro de los límites del periodo especificado.  
  
> [!IMPORTANT]  
>  Si solo busca versiones de fila no actuales, se recomienda usar **CONTAINED IN**, ya que funciona solo con la tabla de historial y producirá el mejor rendimiento de consultas. Use **ALL** cuando necesite consultar datos históricos y actuales sin restricciones.  
  
```  
/* Query using BETWEEN...AND sub-clause*/  
SELECT   
     [DeptID]  
   , [DeptName]  
   , [SysStartTime]  
   , [SysEndTime]  
   , IIF (YEAR(SysEndTime) = 9999, 1, 0) AS IsActual   
FROM [dbo].[Department]   
FOR SYSTEM_TIME BETWEEN  '2015-01-01' AND '2015-12-31'   
WHERE DeptId = 1   
ORDER BY SysStartTime DESC;   
  
/*  Query using CONTAINED IN sub-clause */  
SELECT [DeptID], [DeptName], [SysStartTime],[SysEndTime]   
FROM [dbo].[Department]   
FOR SYSTEM_TIME CONTAINED IN ('2015-04-01', '2015-09-25')   
WHERE DeptId = 1   
ORDER BY SysStartTime DESC ;  
  
/*  Query using ALL sub-clause */   
SELECT    
     [DeptID]   
   , [DeptName]   
   , [SysStartTime]   
   , [SysEndTime]   
   , IIF (YEAR(SysEndTime) = 9999, 1, 0) AS IsActual    
FROM [dbo].[Department] FOR SYSTEM_TIME ALL   
ORDER BY [DeptID], [SysStartTime] Desc  
  
```  
  
## ¿Le ayudó este artículo? Le escuchamos  
 ¿Qué información está buscando? ¿La encontró? Escuchamos sus comentarios para mejorar el contenido. Envíe sus comentarios a [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Queryinging%20a%20System-Versioned%20Temporal%20Table%20page).  
  
## Vea también  
 [Tablas temporales](../../relational-databases/tables/temporal-tables.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)   
 [Creación de una tabla temporal con control de versiones del sistema](../../relational-databases/tables/creating-a-system-versioned-temporal-table.md)   
 [Modificación de los datos de una tabla temporal con control de versiones del sistema](../../relational-databases/tables/modifying-data-in-a-system-versioned-temporal-table.md)   
 [Cambiar el esquema de una tabla temporal con control de versiones del sistema](../../relational-databases/tables/changing-the-schema-of-a-system-versioned-temporal-table.md)   
 [Detención del control de versiones en una tabla temporal con control de versiones](../../relational-databases/tables/stopping-system-versioning-on-a-system-versioned-temporal-table.md)  
  
  