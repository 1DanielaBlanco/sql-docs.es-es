---
title: Método (SQLServerStatement) getWarnings | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerStatement.getWarnings
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3d6decae-2570-4ca5-8ff6-57a2cc3e921f
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b6129d831794a6eaa9c43b2bab53206b10489383
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32838420"
---
# <a name="getwarnings-method-sqlserverstatement"></a>getWarnings (método) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera la primera advertencia que notifica las llamadas en el objeto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public final java.sql.SQLWarning getWarnings()  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Objeto objeto SQLWarning.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método getWarnings es especificado por el método getWarnings en la interfaz java.sql.Statement.  
  
## <a name="see-also"></a>Vea también  
 [Miembros SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Clase SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
