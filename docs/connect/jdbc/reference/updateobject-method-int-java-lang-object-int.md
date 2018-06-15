---
title: Método updateObject (int, java.lang.Object, int) | Documentos de Microsoft
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
- SQLServerResultSet.updateObject (int, java.lang.Object, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9d33571b-4887-49d3-96df-8abda7b5a904
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1f690ba95d40a2e9e43881b0e1c82d497cd5e26d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32849880"
---
# <a name="updateobject-method-int-javalangobject-int"></a>Método updateObject (int, java.lang.Object, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Actualiza la columna designada con un **objeto** valor según el índice de columna y la escala.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public void updateObject(int index,  
                         java.lang.Object x,  
                         int scale)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *index*  
  
 Un **int** que indica el índice de columna.  
  
 *obj*  
  
 Un **objeto** valor.  
  
 *escala*  
  
 Para tipos java.sql.Types.NUMERIC o java.sql.Types.DECIMAL, este es el número de dígitos tras el separador decimal. Para el resto de tipos este valor se omite.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="see-also"></a>Vea también  
 [Método updateObject &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateobject-method-sqlserverresultset.md)   
 [Miembros SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Clase SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
