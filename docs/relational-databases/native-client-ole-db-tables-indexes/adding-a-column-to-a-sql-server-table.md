---
title: Agregar una columna a una tabla de SQL Server | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-tables-indexes
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- AddColumn function
- SQL Server Native Client OLE DB provider, columns
- adding columns
ms.assetid: 22bae18a-bc9d-4617-8660-ed8b17a468d4
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 42ee958f2647a03745259b4a3b975309d515f321
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="adding-a-column-to-a-sql-server-table"></a>Agregar una columna a una tabla de SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client expone la **ITableDefinition:: AddColumn** función. Esto permite que los consumidores agregar una columna a una [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabla.  
  
 Cuando se agrega una columna a una [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabla, el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consumidor del proveedor OLE DB de Native Client se restringe como sigue:  
  
-   Si DBPROP_COL_AUTOINCREMENT es VARIANT_TRUE, DBPROP_COL_NULLABLE debe ser VARIANT_FALSE.  
  
-   Si la columna se define mediante la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp** tipo de datos, DBPROP_COL_NULLABLE debe ser VARIANT_FALSE.  
  
-   Para cualquier otra definición de columna, DBPROP_COL_NULLABLE debe ser VARIANT_TRUE.  
  
 Los consumidores especifican el nombre de tabla como una cadena de caracteres Unicode en el *pwszName* miembro de la *uName* union en la *pTableID* parámetro. El *eKind* miembro de *pTableID* debe ser DBKIND_NAME.  
  
 El nuevo nombre de columna se especifica como una cadena de caracteres Unicode en el *pwszName* miembro de la *uName* union en la *dbcid* miembros del parámetro DBCOLUMNDESC *pColumnDesc*. El *eKind* miembro debe ser DBKIND_NAME.  
  
## <a name="see-also"></a>Vea también  
 [Tablas e índices](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  
  
