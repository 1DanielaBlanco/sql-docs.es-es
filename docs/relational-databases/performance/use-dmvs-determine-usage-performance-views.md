---
title: Uso de DMV para determinar las estadísticas de uso y el rendimiento de las vistas
description: Uso de DMV para determinar las estadísticas de uso y el rendimiento de las vistas
manager: craigg
author: MashaMSFT
ms.author: mathoma
ms.date: 09/27/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.openlocfilehash: 05a02bae41ff2d39d9415154fd1aeabeee065c82
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51668554"
---
# <a name="use-dmvs-to-determine-usage-statistics-and-performance-of-views"></a>Uso de DMV para determinar las estadísticas de uso y el rendimiento de las vistas

Este artículo trata la metodología y los scripts usados para obtener información sobre el **rendimiento de las consultas que utilizan vistas** en un objeto de base de datos. El objetivo de estos scripts es proporcionar los indicadores de uso y el rendimiento de diversas vistas que se encuentran dentro de una base de datos. 

## <a name="sysdmexecqueryoptimizerinfo"></a>Sys.dm_exec_query_optimizer_info

La DMV [sys.dm_exec_query_optimizer_info](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-optimizer-info-transact-sql) expone estadísticas sobre las optimizaciones que ha realizado el optimizador de consultas de SQL Server. Estos valores son acumulativos y empiezan a registrarse cuando se inicia SQL Server.  

La siguiente expresión de tabla común (CTE) usa esta DMV para proporcionar información sobre la carga de trabajo, como el porcentaje de consultas que hacen referencia a una vista. Los resultados que devuelve esta consulta no indican un problema de rendimiento por sí mismos, pero puede exponer los problemas subyacentes cuando se combina con quejas de usuarios relacionadas con el bajo rendimiento de las consultas. 


```SQL
WITH CTE_QO AS
(
  SELECT
    occurrence
  FROM
    sys.dm_exec_query_optimizer_info
  WHERE
    ([counter] = 'optimizations')
),
QOInfo AS
(
  SELECT
    [counter]
    ,[%] = CAST((occurrence * 100.00)/(SELECT occurrence FROM CTE_QO) AS DECIMAL(5, 2))
  FROM
    sys.dm_exec_query_optimizer_info
  WHERE
    [counter] IN ('optimizations'
                  ,'trivial plan'
                  ,'no plan'
                  ,'search 0'
                  ,'search 1'
                  ,'search 2'
                  ,'timeout'
                  ,'memory limit exceeded'
                  ,'insert stmt'
                  ,'delete stmt'
                  ,'update stmt'
                  ,'merge stmt'
                  ,'contains subquery'
                  ,'view reference'
                  ,'remote query'
                  ,'dynamic cursor request'
                  ,'fast forward cursor request'
             )
)
SELECT
  [optimizations] AS [optimizations %]
  ,[trivial plan] AS [trivial plan %]
  ,[no plan] AS [no plan %]
  ,[search 0] AS [search 0 %]
  ,[search 1] AS [search 1 %]
  ,[search 2] AS [search 2 %]
  ,[timeout] AS [timeout %]
  ,[memory limit exceeded] AS [memory limit exceeded %]
  ,[insert stmt] AS [insert stmt %]
  ,[delete stmt] AS [delete stmt]
  ,[update stmt] AS [update stmt]
  ,[merge stmt] AS [merge stmt]
  ,[contains subquery] AS [contains subquery %]
  ,[view reference] AS [view reference %]
  ,[remote query] AS [remote query %]
  ,[dynamic cursor request] AS [dynamic cursor request %]
  ,[fast forward cursor request] AS [fast forward cursor request %]
FROM
  QOInfo
PIVOT (MAX([%]) FOR [counter] 
  IN ([optimizations]
      ,[trivial plan]
      ,[no plan]
      ,[search 0]
      ,[search 1]
      ,[search 2]
      ,[timeout]
      ,[memory limit exceeded]
      ,[insert stmt]
      ,[delete stmt]
      ,[update stmt]
      ,[merge stmt]
      ,[contains subquery]
      ,[view reference]
      ,[remote query]
      ,[dynamic cursor request]
      ,[fast forward cursor request])) AS p;
GO
```
Combine los resultados de esta consulta con los de la vista del sistema [sys.views](https://docs.microsoft.com/sql/relational-databases/system-catalog-views/sys-views-transact-sql) para identificar las estadísticas de consultas, el texto de las consultas y el plan de ejecución almacenado en caché. 

## <a name="sysviews"></a>Sys.views

La siguiente CTE proporciona información sobre el número de ejecuciones, el tiempo de ejecución total y las páginas leídas de la memoria. Los resultados se pueden usar para identificar las consultas que pueden ser candidatas para la optimización. 
  
  >[!NOTE]
  > Los resultados de esta consulta pueden variar según la versión de SQL Server.  


```SQL
WITH CTE_VW_STATS AS
(
  SELECT
    SCHEMA_NAME(vw.schema_id) AS schemaname
    ,vw.name AS viewname
    ,vw.object_id AS viewid
  FROM
    sys.views AS vw
  WHERE
    (vw.is_ms_shipped = 0)
  INTERSECT
  SELECT
    SCHEMA_NAME(o.schema_id) AS schemaname
    ,o.Name AS name
    ,st.objectid AS viewid
  FROM
    sys.dm_exec_cached_plans cp
  CROSS APPLY
    sys.dm_exec_sql_text(cp.plan_handle) st
  INNER JOIN
    sys.objects o ON st.[objectid] = o.[object_id]
  WHERE
    st.dbid = DB_ID()
)
SELECT
  vw.schemaname
  ,vw.viewname
  ,vw.viewid
  ,DB_NAME(t.databaseid) AS databasename
  ,t.databaseid
  ,t.*
FROM
  CTE_VW_STATS AS vw
CROSS APPLY
  (
    SELECT
      st.dbid AS databaseid
      ,st.text
      ,qp.query_plan
      ,qs.*
    FROM
      sys.dm_exec_query_stats AS qs
    CROSS APPLY
      sys.dm_exec_sql_text(qs.plan_handle) AS st
    CROSS APPLY
      sys.dm_exec_query_plan(qs.plan_handle) AS qp
    WHERE
      (CHARINDEX(vw.schemaname, st.text, 1) > 0)
      AND (st.dbid = DB_ID())
  ) AS t;
GO
```

## <a name="sysdmvexeccachedplans"></a>Sys.dmv_exec_cached_plans

La consulta final proporciona información sobre las vistas sin usar mediante la DMV [sys.dmv_exec_cached_plans](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql). Sin embargo, la caché del plan de ejecución es dinámica y los resultados pueden variar. Por lo tanto, use esta consulta con el paso del tiempo para determinar si realmente se utiliza una vista o no. 


```SQL
SELECT
  SCHEMA_NAME(vw.schema_id) AS schemaname
  ,vw.name AS name
  ,vw.object_id AS viewid
FROM
  sys.views AS vw
WHERE
  (vw.is_ms_shipped = 0)
EXCEPT
SELECT
  SCHEMA_NAME(o.schema_id) AS schemaname
  ,o.name AS name
  ,st.objectid AS viewid
FROM
  sys.dm_exec_cached_plans cp
CROSS APPLY
  sys.dm_exec_sql_text(cp.plan_handle) st
INNER JOIN
  sys.objects o ON st.[objectid] = o.[object_id]
WHERE
  st.dbid = DB_ID();
GO
```

## <a name="related-external-resources"></a>Recursos externos relacionados

- [DMVs for Performance Tuning (Video - SQL Saturday Pordenone)](https://www.youtube.com/watch?v=9FQaFwpt3-k) (DMV para ajustes de rendimiento [vídeo: SQL Saturday Pordenone])
- [DMVs for Performance Tuning (Slide e Demo - SQL Saturday Pordenone)](https://www.sqlsaturday.com/589/Sessions/Details.aspx?sid=57409) (DMV para ajustes de rendimiento [diapositivas y demostración: SQL Saturday Pordenone])
- [SQL Server Tuning in capsule form (movie-SQL Saturday Parma)](https://vimeo.com/200980883) (Ajustes en SQL Server con pequeños ejemplos [vídeo: SQL Saturday Parma])
- [SQL Server Tuning in a nutshell (slides and Demo-SQL Saturday Parma)](https://www.sqlsaturday.com/566/Sessions/Details.aspx?sid=53988) (Ajustes en SQL Server: resumen [SQL Saturday Parma])
- [Performance Tuning With SQL Server Dynamic Management Views](https://www.red-gate.com/library/performance-tuning-with-sql-server-dynamic-management-views) (Ajustes de rendimiento con las vistas de administración dinámicas de SQL Server)
- [The Most Prominent Wait Types of your SQL Server 2016](https://channel9.msdn.com/Blogs/MVP-Data-Platform/The-Most-Prominent-Wait-Types-of-your-SQL-Server-2016) (Los tipos de espera más importantes de SQL Server 2016)
