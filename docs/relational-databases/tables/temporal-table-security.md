---
title: Seguridad de la tabla temporal | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 02/21/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60e5d6f6-a26d-4bba-aada-42e382bbcd38
caps.latest.revision: 9
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f73cdc0f3a240e3d4c795fd67c2913b99748de4a
ms.contentlocale: es-es
ms.lasthandoff: 04/11/2017

---
# <a name="temporal-table-security"></a>Seguridad de la tabla temporal
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Para comprender la seguridad en relación con las tablas temporales, conviene entender los principios de seguridad que se aplican a las dichas tablas. Una vez que comprenda estos principios de seguridad, estará listo para profundizar en la seguridad de las instrucciones **CREATE TABLE**, **ALTER TABLE**y **SELECT** .  
  
## <a name="security-principles"></a>Principios de seguridad  
 En la siguiente tabla se describen los principios de seguridad que se aplican a las tablas temporales:  
  
|Principio|Descripción|  
|---------------|-----------------|  
|La habilitación o deshabilitación del control de versiones del sistema requiere los privilegios más altos en los objetos afectados.|Para habilitar y deshabilitar SYSTEM_VERSIONING, se requiere el permiso CONTROL en la tabla actual y de historial.|  
|Los datos del historial no se pueden modificar directamente.|Cuando SYSTEM_VERSIONING tenga el valor ON, los usuarios no podrán modificar los datos del historial, con independencia de los permisos que tengan en la tabla actual o de historial. Se incluyen las modificaciones de datos y esquema.|  
|Para consultar datos del historial se requiere el permiso **SELECT** en la tabla de historial.|Solo porque un usuario tenga el permiso **SELECT** en la tabla actual no significa que disfrutará del permiso **SELECT** en la de historial.|  
|En la auditoría se muestran las operaciones que afectan a la tabla de historial de forma específica:|La auditoría de la tabla de historial capta de forma regular todos los intentos directos de acceder a los datos (al margen de si se produjeron correctamente o no).<br /><br /> El permiso**SELECT** con la extensión de consulta temporal muestra que esa operación afectó a la tabla de historial.<br /><br /> La instrucción**CREATE/ALTER** para una tabla temporal expone información según la que la comprobación de permisos también tiene lugar en la tabla del historial. El archivo de auditoría contendrá un registro adicional para la tabla de historial.<br /><br /> Las operaciones DML efectuadas en la tabla actual muestran que la de historial se vio afectada, pero additional_info ofrece el contexto necesario (DML fue el resultado de system_versioning).|  
  
## <a name="performing-schema-operations"></a>Realización de operaciones de esquema  
 Cuando SYSTEM_VERSIONING esté establecido en ON, las operaciones de modificación de esquema son limitadas.  
  
### <a name="disallowed-alter-schema-operations"></a>Operaciones de esquema ALTER no permitidas.  
  
|Operación|Tabla actual|Tabla de historial|  
|---------------|-------------------|-------------------|  
|**DROP TABLE**|No permitida.|No permitida.|  
|**ALTER TABLE…SWITCH PARTITION**|Solo SWITCH IN; vea [Partitioning with Temporal Tables](../../relational-databases/tables/partitioning-with-temporal-tables.md)(Creación de particiones con tablas temporales)|Solo SWITCH OUT; vea [Partitioning with Temporal Tables](../../relational-databases/tables/partitioning-with-temporal-tables.md)(Creación de particiones con tablas temporales)|  
|**ALTER TABLE…DROP PERIOD**|No permitida.|-|  
|**ALTER TABLE…ADD PERIOD**|-|No permitida.|  
  
## <a name="allowed-alter-table-operations"></a>Operaciones ALTER TABLE permitidas  
  
|Operación|Current|Historial|  
|---------------|-------------|-------------|  
|**ALTER TABLE…REBUILD**|Permitida (independientemente)|Permitida (independientemente)|  
|**CREATE INDEX**|Permitida (independientemente)|Permitida (independientemente)|  
|**CREATE STATISTICS**|Permitida (independientemente)|Permitida (independientemente)|  
  
## <a name="security-of-the-create-temporal-table-statement"></a>Seguridad de la instrucción CREATE TABLE (tabla temporal)  
  
||Crear una nueva tabla de historial|Volver a usar la tabla de historial existente|  
|-|------------------------------|----------------------------------|  
|Permiso necesario|El permiso**CREATE TABLE** en la base de datos.<br /><br /> El permiso**ALTER** en los esquemas en los que se están creando las tablas actuales y de historial.|El permiso**CREATE TABLE** en la base de datos.<br /><br /> El permiso**ALTER** en el esquema en el que se creará la tabla actual.<br /><br /> El permiso**CONTROL** en la tabla de historial especificada como parte de la instrucción **CREATE TABLE** que crea la tabla temporal.|  
|Auditar|En la auditoría se muestra que los usuarios trataron de crear dos objetos. La operación puede producir un error debido a una falta de permisos para crear la tabla en la base de datos o modificar esquemas para cualquiera de las dos tablas.|En la auditoría se muestra que la tabla temporal se creó. La operación puede generar un error debido a la falta de permisos para crear una tabla en la base de datos o alterar el esquema para la tabla temporal, o bien que no se dispongan que los permisos suficientes en la tabla de historial.|  
  
## <a name="security-of-the-alter-temporal-table-set-systemversioning-onoff-statement"></a>Seguridad de la instrucción ALTER TABLE SET (tabla temporal) (SYSTEM_VERSIONING ON/OFF)  
  
||Crear una nueva tabla de historial|Volver a usar la tabla de historial existente|  
|-|------------------------------|----------------------------------|  
|Permiso necesario|El permiso**CONTROL** en la base de datos.<br /><br /> El permiso**CREATE TABLE** en la base de datos.<br /><br /> El**ALTER** permiso en los esquemas en los que se está creando la tabla de historial.|El permiso**CONTROL** en la tabla original que se ha modificado.<br /><br /> El permiso**CONTROL** en la tabla de historial especificada como parte de la instrucción **ALTER TABLE** .|  
|Auditar|En la auditoría se muestra que se modificó la tabla temporal y que la de historial se creó a la vez. La operación puede generar un error debido a la falta de permisos para crear una tabla en la base de datos, alterar el esquema para la tabla de historial o modificar la tabla de temporal.|En la auditoría se muestra que se modificó la tabla temporal, pero que la operación requería acceso a la de historial. La operación puede generar un error debido a una falta de permisos en la tabla de historial o en la actual.|  
  
## <a name="security-of-select-statement"></a>Seguridad de la instrucción SELECT  
 El permiso**SELECT** no cambia para las instrucciones **SELECT** que no afectan a la tabla de historial. En lo que respecta a las instrucciones **SELECT** que afectan a la tabla de historial, se requiere el permiso **SELECT** en la tabla actual y de historial.  
  
## <a name="did-this-article-help-you-were-listening"></a>¿Le ayudó este artículo? Le escuchamos  
 ¿Qué información está buscando? ¿La encontró? Escuchamos sus comentarios para mejorar el contenido. Envíe sus comentarios a [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Temporal%20Table%20Security%20page)  
  
## <a name="see-also"></a>Vea también  
 [Tablas temporales](../../relational-databases/tables/temporal-tables.md)   
 [Introducción a las tablas temporales con versión del sistema](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [Comprobaciones de coherencia del sistema de la tabla temporal](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [Creación de particiones con tablas temporales](../../relational-databases/tables/partitioning-with-temporal-tables.md)   
 [Limitaciones y consideraciones de las tablas temporales](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)   
 [Administración de la retención de datos históricos en las tablas temporales con versiones del sistema](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Tablas temporales con control de versiones del sistema con tablas con optimización para memoria](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Funciones y vistas de metadatos de la tabla temporal](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  

