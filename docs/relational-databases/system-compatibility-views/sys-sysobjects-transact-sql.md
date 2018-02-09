---
title: Sys.sysobjects (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sysobjects_TSQL
- sysobjects
- sysobjects_TSQL
- sys.sysobjects
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysobjects compatibility view
- sysobjects system table
ms.assetid: 44fdc387-67b0-4139-8bf5-ed26cf640cd1
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 58b3ba692fd946c15e3f00a7d1179f10df5d0b37
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="syssysobjects-transact-sql"></a>sys.sysobjects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Contiene una fila por cada objeto creado en una base de datos, como restricciones, valores predeterminados, registros, reglas y procedimientos almacenados.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nombre de columna|Tipo de datos|Description|  
|-----------------|---------------|-----------------|  
|name|**sysname**|Nombre del objeto|  
|id|**int**|Número de identificación de objeto|  
|xtype|**char(2)**|Tipo de objeto. Puede ser uno de los siguientes tipos de objeto:<br /><br /> AF = Función de agregado (CLR)<br /><br /> C = restricción CHECK<br /><br /> D = Valor predeterminado o restricción DEFAULT<br /><br /> F = Restricción FOREIGN KEY<br /><br /> L = Registro<br /><br /> FN = Función escalar<br /><br /> FS = Función escalar del ensamblado (CLR)<br /><br /> FT = Función con valores de tabla de ensamblado (CLR)<br /><br /> IF = Función de tabla en línea<br /><br /> IT = tabla interna<br /><br /> P = Procedimiento almacenado<br /><br /> PC = Procedimiento almacenado del ensamblado (CLR)<br /><br /> PK = Restricción PRIMARY KEY (de tipo K)<br /><br /> RF = Procedimiento almacenado de filtro de replicación<br /><br /> S = Tabla del sistema<br /><br /> SN = Sinónimo<br /><br /> SQ = Cola de servicio<br /><br /> TA = Desencadenador DML del ensamblado (CLR)<br /><br /> TF = Función de tabla<br /><br /> TR = desencadenador DML SQL<br /><br /> TT = Tipo de tabla<br /><br /> U = Tabla de usuario<br /><br /> UQ = Restricción UNIQUE (de tipo K)<br /><br /> V = Vista<br /><br /> X = Procedimiento almacenado extendido|  
|uid|**smallint**|Identificador de esquema del propietario del objeto. Para bases de datos actualizadas a partir de una versión anterior de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], el identificador de esquema es igual que el identificador de usuario del propietario. Produce un desbordamiento o devuelve NULL si el número de usuarios y roles es superior a 32.767.<br /><br /> **\*\*Importante \* \***  si utiliza alguna de las siguientes acciones [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instrucciones DDL, debe utilizar el [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) vista en lugar de sys.sysobjects de catálogo.<br /><br /> CREAR &#124; ALTER &#124; QUITE EL USUARIO<br /><br /> CREAR &#124; ALTER &#124; QUITAR ROL<br /><br /> CREAR &#124; ALTER &#124; QUITAR ROL DE APLICACIÓN<br /><br /> CREATE SCHEMA<br /><br /> ALTER AUTHORIZATION ON OBJECT|  
|info|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|status|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|base_schema_ver|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|replinfo|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|parent_obj|**int**|Número de identificación del objeto primario. Por ejemplo, el identificador de tabla si es un desencadenador o una restricción.|  
|crdate|**datetime**|Fecha de creación del objeto.|  
|ftcatid|**smallint**|Identificador del catálogo de texto completo de todas las tablas de usuario registradas para la indización de texto completo y 0 para todas las tablas de usuario no registradas.|  
|schema_ver|**int**|Número de versión que se incrementa cada vez que cambia el esquema de una tabla. Siempre devuelve 0.|  
|stats_schema_ver|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|tipo|**char(2)**|Tipo de objeto. Puede ser uno de los siguientes valores:<br /><br /> AF = Función de agregado (CLR)<br /><br /> C = restricción CHECK<br /><br /> D = Valor predeterminado o restricción DEFAULT<br /><br /> F = Restricción FOREIGN KEY<br /><br /> FN = Función escalar<br /><br /> FS = Función escalar del ensamblado (CLR)<br /><br /> FT = Función con valores de tabla de ensamblado (CLR) IF = Función de tabla en línea<br /><br /> IT = Tabla interna<br /><br /> K = Restricción PRIMARY KEY o UNIQUE<br /><br /> L = Registro<br /><br /> P = Procedimiento almacenado<br /><br /> PC = Procedimiento almacenado del ensamblado (CLR)<br /><br /> R = Regla<br /><br /> RF = Procedimiento almacenado de filtro de replicación<br /><br /> S = Tabla del sistema<br /><br /> SN = Sinónimo<br /><br /> SQ = Cola de servicio<br /><br /> TA = Desencadenador DML del ensamblado (CLR)<br /><br /> TF = Función de tabla<br /><br /> TR = desencadenador DML SQL<br /><br /> TT = Tipo de tabla<br /><br /> U = Tabla de usuario<br /><br /> V = Vista<br /><br /> X = Procedimiento almacenado extendido|  
|userstat|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|sysstat|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|indexdel|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|refdate|**datetime**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|version|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|deltrig|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|instrig|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|updtrig|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|seltrig|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|category|**int**|Utilizado para publicación, restricciones e identidad.|  
|caché|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>Vea también  
 [Asignar tablas del sistema a vistas del sistema &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Vistas de compatibilidad &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
