---
title: "Método getCharacterStream (long, long) (SQLServerNClob) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a8028bc-c877-4668-b662-0746d462040e
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ee42e6ef541b8f3c8298d467b6eb72237016efb4
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="getcharacterstream-method-long-long-sqlservernclob"></a>Método getCharacterStream (long, long) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera el **NCLOB** datos como un **lector** objeto o como una secuencia de caracteres con una posición y longitud especificadas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public java.io.Reader getCharacterStream(long pos,  
                                  long length)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *punto de venta*  
  
 A **largo** que indica el desplazamiento hasta el primer carácter del valor parcial que se va a recuperar.  
  
 *length*  
  
 A **largo** que indica la longitud en caracteres del valor parcial que se va a recuperar.  
  
## <a name="return-value"></a>Valor devuelto  
 Un objeto de lector que contiene el **NCLOB** datos.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método getCharacterStream especificado por el método getCharacterStream en la interfaz java.sql.NClob.  
  
## <a name="see-also"></a>Vea también  
 [Método getCharacterStream &#40; SQLServerNClob &#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlservernclob.md)   
 [Métodos SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Miembros de SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Clase SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
