---
title: Recibir varios conjuntos de registros | Documentos de Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receiving multiple Recordsets [ADO]
- Recordset object [ADO], receiving multiple Recordsets
ms.assetid: 2a7ad7a6-f00d-4355-b0b5-d0ab957b0566
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3687e3ee6a2588a5461e48a1f3f26db91d14a8fb
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="receiving-multiple-recordsets"></a>Recibir varios conjuntos de registros
El [proveedor Microsoft OLE DB para SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) admite devolver varios **Recordset** objetos de un comando único que contiene varias instrucciones SQL, una **Recordset**por la instrucción SQL. El orden en que el **Recordset**se devolverán sigue el orden en que las instrucciones SQL se colocan en el texto del comando.  
  
 El proveedor Microsoft OLE DB para SQL Server también devuelve varios conjuntos de resultados a ADO cuando el comando contiene una cláusula COMPUTE. Por ejemplo, un comando que contiene la instrucción SQL siguiente devolverá los resultados en dos **Recordset** objetos: uno para el conjunto de filas de (*ProductID*, *ProductName*, *UnitPrice*) y otro para el precio medio de todos los productos de la tabla.  
  
```  
SELECT ProductID, ProductName, UnitPrice   
  FROM PRODUCTS   
  COMPUTE AVG(UnitPrice)  
```  
  
 Puede usar el **Recordset.NextRecordset** método para enumerar los dos objetos.  
  
 Para obtener más información, consulte [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md).
