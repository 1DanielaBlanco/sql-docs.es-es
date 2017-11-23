---
title: "Quitar un índice de SQL Server | Documentos de Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: add3ba14-10b1-4723-b7c0-3e83689e9fdd
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 745951f7c4a1436a5bae36db24d3431d1a4e64a4
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="dropping-a-sql-server-index"></a>Quitar un índice de SQL Server
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client expone la **IIndexDefinition:: DropIndex** función. Esto permite que los consumidores puedan quitar un índice de un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabla.  
  
 El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client expone algunas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restricciones PRIMARY KEY y UNIQUE como índices. Pueden modificar el propietario de la tabla, el propietario de la base de datos y algunos miembros del rol administrativo un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabla, quitar una restricción. De forma predeterminada, solo el propietario de la tabla puede quitar un índice existente. Por lo tanto, **DropIndex** finalizó correctamente o no depende no solo de derechos de acceso del usuario de la aplicación sino también en el tipo de índice indicado.  
  
 Los consumidores especifican el nombre de tabla como una cadena de caracteres Unicode en el *pwszName* miembro de la *uName* union en la *pTableID* parámetro. El *eKind* miembro de *pTableID* debe ser DBKIND_NAME.  
  
 Los consumidores especifican el nombre del índice como una cadena de caracteres Unicode en el *pwszName* miembro de la *uName* union en la *pIndexID* parámetro. El *eKind* miembro de *pIndexID* debe ser DBKIND_NAME. El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client no admite la característica de OLE DB de quitar todos los índices en una tabla cuando *pIndexID* es null. Si *pIndexID* es null, se devuelve E_INVALIDARG.  
  
## <a name="see-also"></a>Vea también  
 [Tablas e índices](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-index-transact-sql.md)  
  
  
