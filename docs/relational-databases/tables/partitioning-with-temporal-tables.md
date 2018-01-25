---
title: "Creación de particiones con tablas temporales | Microsoft Docs"
ms.custom: 
ms.date: 04/26/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: tables
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 313714b8-4ad1-4c14-93a3-7f628a334a51
caps.latest.revision: "11"
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a231d7b2b3290747d37faf4eb6fe4c46f0d1f174
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/18/2018
---
# <a name="partitioning-with-temporal-tables"></a>Creación de particiones con tablas temporales
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Puede usar la creación de particiones en la tabla actual y en la tabla de historial de forma independiente. Sin embargo, la creación de particiones no puede utilizarse para cambiar el contenido de los datos sin el control de versiones del sistema.  
  
> [!NOTE]  
>  La creación de particiones es una característica de SQL Server 2016 Enterprise Edition anterior a Service Pack 1 y versiones anteriores. Esta característica se admite en todas las ediciones de SQL Server 2016 Service Pack 1 y en versiones posteriores.
  
-   **Tabla actual:**  
  
    -   **SWITCH IN** a la tabla actual se puede usar para facilitar la carga y la consulta de datos mientras **SYSTEM_VERSIONING** está **ON**  
  
    -   **SWITCH OUT** no está permitido mientras **SYSTEM_VERSIONING** está **ON**  
  
-   **Tabla de historial:**  
  
    -   **SWITCH OUT** desde la tabla de historial se puede realizar mientras **SYSTEM_VERSIONING** está **ON** para purgar las partes de datos del historial que ya no sean de interés.  
  
    -   **SWITCH IN** no se permite mientras **SYSTEM_VERSIONING** está **ON** , puesto que puede invalidar la coherencia de los datos temporales.  
  
## <a name="did-this-article-help-you-were-listening"></a>¿Le ayudó este artículo? Le escuchamos  
 ¿Qué información está buscando? ¿La encontró? Escuchamos sus comentarios para mejorar el contenido. Envíe sus comentarios a [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Partitioning%20with%20Temporal%20Tables%20page)  
  
## <a name="see-also"></a>Ver también  
 [Tablas temporales](../../relational-databases/tables/temporal-tables.md)   
 [Introducción a las tablas temporales con versión del sistema](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [Comprobaciones de coherencia del sistema de la tabla temporal](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [Limitaciones y consideraciones de las tablas temporales](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)   
 [Seguridad de la tabla temporal](../../relational-databases/tables/temporal-table-security.md)   
 [Administración de la retención de datos históricos en las tablas temporales con versiones del sistema](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Tablas temporales con control de versiones del sistema con tablas con optimización para memoria](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Funciones y vistas de metadatos de la tabla temporal](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  
