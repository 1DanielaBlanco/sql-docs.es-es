---
title: "Establecer la opci&#243;n de configuraci&#243;n del servidor Grado m&#225;ximo de paralelismo | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "consultas en paralelo [SQL Server]"
  - "procesadores [SQL Server], consultas en paralelo"
  - "número de procesadores para consultas en paralelo"
  - "max degree of parallelism, opción"
ms.assetid: 86b65bf1-a6a1-4670-afc0-cdfad1558032
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# Establecer la opci&#243;n de configuraci&#243;n del servidor Grado m&#225;ximo de paralelismo
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  En este tema se describe cómo establecer la opción de configuración del servidor **grado máximo de paralelismo (MAXDOP)** en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Cuando una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se ejecuta en un equipo con más de un microprocesador o CPU, detecta el mejor grado de paralelismo, es decir, el número de procesadores que se emplea para ejecutar una única instrucción en cada ejecución de planes en paralelo. Puede utilizar la opción **max degree of parallelism** (grado máximo de paralelismo) para limitar el número de procesadores que debe utilizarse en la ejecución de planes en paralelo. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] considera los planes de ejecución en paralelo para las consultas, las operaciones de lenguaje de definición de datos (DDL) de índice, la inserción en paralelo, la modificación de columna en línea, la colección de estadísticas en paralelo y el rellenado de cursor estático y controlado por conjuntos de claves.
 

  
  
##  <a name="BeforeYouBegin"></a> Antes de empezar  
  
###  <a name="Restrictions"></a> Limitaciones y restricciones  
  
-   Si el valor de la opción affinity mask no es el predeterminado, es posible que se limite el número de procesadores disponibles para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en sistemas de multiproceso simétrico (SMP).  
  
###  <a name="Recommendations"></a> Recomendaciones  
  
-   Esta opción es avanzada y solo debe cambiarla un administrador de base de datos con experiencia o un técnico de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con la titulación apropiada.  
  
-   Para que el servidor pueda determinar el Grado máximo de paralelismo, establezca esta opción en 0, que es el valor predeterminado. Si se establece el grado máximo de paralelismo en 0, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] puede usar todos los procesadores disponibles hasta un número de 64. Para suprimir la generación de planes paralelos, establezca la opción **max degree of parallelism** en 1. Establezca el valor en un número de 1 a 32.767 para especificar el número máximo de núcleos de procesador que puede usar una única ejecución de consulta. Si se especifica un valor superior al número de procesadores disponibles, se utilizará el número real de procesadores disponibles. Si el equipo tiene solo un procesador, el valor de **grado máximo de paralelismo** se pasará por alto.  
  
-   Puede omitir el valor de la opción max degree of parallelism especificando la sugerencia de consulta MAXDOP en la instrucción de la consulta. Para obtener más información, vea [Sugerencias de consulta &#40;Transact-SQL&#41;](../Topic/Query%20Hints%20\(Transact-SQL\).md).  
  
-   Las operaciones de índice que crean o vuelven a generar un índice, o que eliminan un índice clúster, pueden consumir recursos de forma intensiva. Puede omitir el valor de la opción max degree of parallelism para operaciones de índice especificando la opción de índice MAXDOP en la instrucción del índice.  El valor de MAXDOP se aplica a la instrucción en tiempo de ejecución y no se almacena en los metadatos del índice. Para obtener más información, vea [Configurar operaciones de índice en paralelo](../../relational-databases/indexes/configure-parallel-index-operations.md).  
  
-   Además de las operaciones de consultas e índices, esta opción también controla el paralelismo de DBCC CHECKTABLE, DBCC CHECKDB y DBCC CHECKFILEGROUP. Puede deshabilitar los planes de ejecución en paralelo de estas instrucciones mediante el uso de la marca de seguimiento 2528. Para obtener más información, vea [Marcas de seguimiento &#40;Transact-SQL&#41;](../Topic/Trace%20Flags%20\(Transact-SQL\).md).  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 De forma predeterminada, todos los usuarios tienen permisos de ejecución en **sp_configure** sin ningún parámetro o solo con el primero. Para ejecutar **sp_configure** con ambos parámetros y cambiar una opción de configuración, o para ejecutar la instrucción RECONFIGURE, un usuario debe tener el permiso ALTER SETTINGS en el nivel de servidor. Los roles fijos de servidor **sysadmin** y **serveradmin** tienen el permiso ALTER SETTINGS de forma implícita.  
  
##  <a name="SSMSProcedure"></a> Usar SQL Server Management Studio  
  
#### Para configurar la opción de grado máximo de paralelismo  
  
1.  En el **Explorador de objetos**, haga clic con el botón derecho en un servidor y seleccione **Propiedades**.  
  
2.  Haga clic en el nodo **Avanzado** .  
  
3.  En el cuadro **Grado máximo de paralelismo** , seleccione el número máximo de procesadores que se usarán en la ejecución de planes paralelos.  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
  
#### Para configurar la opción de grado máximo de paralelismo  
  
1.  Conéctese con el [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  En la barra Estándar, haga clic en **Nueva consulta**.  
  
3.  Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**. En este ejemplo se muestra cómo usar [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) para configurar la opción de `max degree of parallelism` en `8`.  
  
```tsql  
USE AdventureWorks2012 ;  
GO   
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
EXEC sp_configure 'max degree of parallelism', 8;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
```  
  
 Para obtener más información, vea [Opciones de configuración de servidor &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Seguimiento: Después de configurar la opción de grado máximo de paralelismo  
 La configuración surte efecto inmediatamente, sin necesidad de reiniciar el servidor.  
  
## Vea también  
 [affinity mask (opción de configuración del servidor)](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Opciones de configuración de servidor &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [DBCC CHECKTABLE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md)   
 [DBCC CHECKDB &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)   
 [DBCC CHECKFILEGROUP &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkfilegroup-transact-sql.md)   
 [Configurar operaciones de índice en paralelo](../../relational-databases/indexes/configure-parallel-index-operations.md) 
 [Sugerencias de consulta &#40;Transact-SQL&#41;](../Topic/Query%20Hints%20\(Transact-SQL\).md)    
 [Establecer opciones de índice](../../relational-databases/indexes/set-index-options.md)  
  
  