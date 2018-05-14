---
title: Migración de desencadenadores | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: in-memory-oltp
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ad5385c5-5a50-40ca-a319-97d5606b8511
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 1c1fa55130e7e750a0cccda7d81559bd5ffd71ac
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="migrating-triggers"></a>Migrar desencadenadores
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  En este tema se describen los desencadenadores DDL y las tablas optimizadas para memoria.  
  
 Se admiten los desencadenadores DML en tablas optimizadas en memoria, pero solo con el evento de desencadenador FOR | AFTER. Para obtener un ejemplo, vea [Implementación de UPDATE con FROM o subconsultas](../../relational-databases/in-memory-oltp/implementing-update-with-from-or-subqueries.md). 
  
 Los desencadenadores LOGON son desencadenadores definidos para activarse en eventos LOGON. Los desencadenadores LOGON no afectan a las tablas optimizadas para memoria.  
  
## <a name="ddl-triggers"></a>Desencadenadores DDL  
 Los desencadenadores DDL son desencadenadores definidos para activarse cuando se ejecuta una instrucción CREATE, ALTER, DROP, GRANT, DENY, REVOKE o UPDATE STATISTICS en la base de datos o el servidor en el que se define.  
  
 No se pueden crear tablas optimizadas para memoria si la base de datos o el servidor tiene uno o varios desencadenadores DDL definidos en CREATE_TABLE o en cualquier grupo de eventos que lo incluyan. No se puede quitar una tabla optimizada para memoria si la base de datos o el servidor tiene uno o varios desencadenadores DDL definidos en DROP_TABLE o en cualquier grupo de eventos que lo incluyan.  
  
 No se pueden crear procedimientos almacenados compilados de forma nativa si hay uno o más desencadenadores DDL en CREATE_PROCEDURE, DROP_PROCEDURE o cualquier grupo de eventos que incluya los eventos.  
  
## <a name="see-also"></a>Ver también  
 [Migrar a OLTP en memoria](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  
