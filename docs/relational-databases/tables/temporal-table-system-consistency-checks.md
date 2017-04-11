---
title: "Comprobaciones de coherencia del sistema de la tabla temporal | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/07/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec081d42-57e4-43c7-9e1c-317ba8f23437
caps.latest.revision: 10
author: "CarlRabeler"
ms.author: "carlrab"
manager: "jhubbard"
caps.handback.revision: 10
---
# Comprobaciones de coherencia del sistema de la tabla temporal
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Cuando se usan tablas temporales, el sistema realiza una serie de comprobaciones de coherencia para asegurarse de que el esquema cumple los requisitos de temporalidad y que los datos son y se mantienen coherentes. Además, se han agregado comprobaciones temporales a la instrucción **DBCC CHECKCONSTRAINTS** .  
  
## Comprobaciones de coherencia del sistema  
 Antes de establecer **SYSTEM_VERSIONING** en **ON**, se llevan a cabo un conjunto de comprobaciones en la tabla de historial y en la tabla actual. Estas comprobaciones se agrupan en comprobaciones de esquemas y comprobaciones de datos (si la tabla de historial no está vacía). Además, el sistema también realiza una comprobación de coherencia en tiempo de ejecución.  
  
### Comprobación de esquema  
 Al crear o modificar una tabla para convertirla en una tabla temporal, el sistema comprueba que se cumplan una serie de requisitos:  
  
1.  El nombre y el número de columnas es el mismo en la tabla actual y en la tabla de historial.  
  
2.  Los tipos de datos de cada columna coinciden entre la tabla actual y la tabla de historial.  
  
3.  Las columnas de período se establecen en **NOT NULL**.  
  
4.  La tabla actual tiene una restricción de clave principal, mientras que la tabla de historial no la tiene.  
  
5.  En la tabla de historial no hay definida ninguna columna **IDENTITY** .  
  
6.  En la tabla de historial no hay definidos desencadenadores.  
  
7.  En la tabla de historial no hay definidas claves externas.  
  
8.  En la tabla de historial no hay definidas restricciones de tabla o columna. Sin embargo, en la tabla de historial se permiten valores de columna predeterminados.  
  
9. La tabla de historial no está ubicada en un grupo de archivos de solo lectura.  
  
10. La tabla de historial no está configurada para el seguimiento de cambios o la captura de datos modificados.  
  
### Comprobación de coherencia de datos  
 Antes de que **SYSTEM_VERSIONING** se establezca en **ON** y como parte de cualquier operación de DML, el sistema realiza la comprobación siguiente: **SysEndTime** ≥**SysStartTime**  
  
 Al crear un vínculo a una tabla de historial existente, puede realizar una comprobación de coherencia de datos. La comprobación de coherencia de datos garantiza que los registros existentes no se superponen y que cada registro cumple los requisitos temporales. La comprobación de coherencia de datos se realiza de manera predeterminada. Por lo general, se recomienda realizar esta comprobación siempre que los datos entre la tabla actual y la de historial puedan no estar sincronizados, por ejemplo, cuando se incorpora una tabla de historial existente que se rellena con datos del historial.  
  
> [!WARNING]  
>  Si se cambia manualmente la hora del reloj del sistema, el sistema fallará inesperadamente porque se producirá un error en las comprobaciones de coherencia de datos en tiempo de ejecución que se aplican para evitar condiciones de superposición (es decir, que la hora de finalización de un registro no sea anterior a su hora de inicio).  
  
## DBCC CHECKCONSTRAINTS  
 El comando **DBCC CHECKCONSTRAINTS** incluye comprobaciones de coherencia de datos temporales. Para obtener más información, vea [DBCC CHECKCONSTRAINTS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkconstraints-transact-sql.md).  
  
## ¿Le ayudó este artículo? Le escuchamos  
 ¿Qué información está buscando? ¿La encontró? Escuchamos sus comentarios para mejorar el contenido. Envíe sus comentarios a [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Temporal%20Table%20System%20Consistency%20Checks%20page).  
  
## Vea también  
 [Tablas temporales](../../relational-databases/tables/temporal-tables.md)   
 [Introducción a las tablas temporales con versión del sistema](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [Creación de particiones con tablas temporales](../../relational-databases/tables/partitioning-with-temporal-tables.md)   
 [Limitaciones y consideraciones de las tablas temporales](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)   
 [Seguridad de la tabla temporal](../../relational-databases/tables/temporal-table-security.md)   
 [Administración de la retención de datos históricos en las tablas temporales con versiones del sistema](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Tablas temporales con control de versiones del sistema con tablas con optimización para memoria](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Funciones y vistas de metadatos de la tabla temporal](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  