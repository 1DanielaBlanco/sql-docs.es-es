---
title: Modificar módulos T-SQL compilados de forma nativa | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 010318a0-6807-47c3-8ecc-bb7cb60513f0
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8e6229b5b7c8ad03b6a8fbabb317d470eadb4c69
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="altering-natively-compiled-t-sql-modules"></a>Altering Natively Compiled T-SQL Modules
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  En [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] (y versiones posteriores) y [!INCLUDE[ssSDS](../../includes/sssds-md.md)] puede realizar operaciones ALTER en procedimientos almacenados compilados de forma nativa y otros módulos T-SQL compilados de forma nativa como UDF escalares y desencadenadores mediante la instrucción ALTER.  
  
 Al ejecutar ALTER en un módulo T-SQL compilado de forma nativa, el módulo se vuelve a compilar con una nueva definición. Mientras la recompilación está en curso, la versión antigua del módulo sigue estando disponible para su ejecución. Una vez completada la compilación, se agotan las ejecuciones del módulo y se instala la nueva versión del módulo. Cuando se modifica un módulo T-SQL compilado de forma nativa, puede modificar las opciones siguientes.  
  
-   Parámetros  
  
-   EXECUTE AS  
  
-   NIVEL DE AISLAMIENTO DE TRANSACCIÓN  
  
-   LANGUAGE  
  
-   DATEFIRST  
  
-   DATEFORMAT  
  
-   DELAYED_DURABILITY  
  
> [!NOTE]  
>  No es posible convertir módulos T-SQL compilados de forma nativa en módulos compilados de forma no nativa. No es posible convertir módulos T-SQL compilados de forma no nativa en módulos compilados de forma nativa.  
  
 Para obtener más información sobre la funcionalidad y la sintaxis de ALTER PROCEDURE, vea [ALTER PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-procedure-transact-sql.md).  
  
 Si ejecuta sp_recompile en un módulo T-SQL compilado de forma nativa, hará que se vuelva a compilar en la siguiente ejecución.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea una tabla optimizada para memoria (T1) y un procedimiento almacenado compilado de forma nativa (SP1) que selecciona todas las columnas de T1. Después, se modifica SP1 para quitar la cláusula EXECUTE AS, cambiar el valor de LANGUAGE y seleccionar una sola columna (C1) de T1.  
  
```  
CREATE TABLE [dbo].[T1]  
(  
[c1] [int] NOT NULL,  
[c2] [float] NOT NULL,  
CONSTRAINT [PK_T1] PRIMARY KEY NONCLUSTERED ([c1])  
)WITH ( MEMORY_OPTIMIZED = ON , DURABILITY = SCHEMA_AND_DATA )  
GO  
  
CREATE PROCEDURE [dbo].[usp_1]  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH  
(  
 TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english'  
)  
 SELECT c1, c2 from dbo.T1  
END  
GO  
  
ALTER PROCEDURE [dbo].[usp_1]  
WITH NATIVE_COMPILATION, SCHEMABINDING  
AS BEGIN ATOMIC WITH  
(  
 TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'Dutch'  
)  
 SELECT c1 from dbo.T1  
END  
GO  
  
```  
  
  
