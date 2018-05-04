---
title: María getResponseBuffering (SQLServerStatement) | Documentos de Microsoft
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
- SQLServerStatement.getResponseBuffering()
apilocation:
- SQLServerStatement.getResponseBuffering()
apitype: Assembly
ms.assetid: a9a9ffdd-7ce3-4e0a-907c-34d6a54e6865
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 64ad84e838e64c0e4bd148705e2753277f908a3c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="getresponsebuffering-method-sqlserverstatement"></a>María getResponseBuffering (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera la respuesta el modo de almacenamiento en búfer para esta [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public final java.lang.String getResponseBuffering()  
```  
  
## <a name="return-value"></a>Valor devuelto  
 A **cadena** que contiene una minúscula **completa** o **adaptable**.  
  
## <a name="remarks"></a>Comentarios  
 **adaptable** especifica el almacenamiento en búfer los datos mínimos posibles cuando sea necesario.  
  
 **completa** especifica leer el resultado completo desde el servidor en tiempo de ejecución.  
  
 **adaptable** es el valor predeterminado en la versión 2.0 y 3.0 del controlador JDBC. **completa** era la predeterminada antes de la versión 2.0 del controlador JDBC.  
  
 Para obtener más información acerca de cómo utilizar el modo de almacenamiento en búfer de respuesta, consulte [usar almacenamiento en búfer adaptable](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>Vea también  
 [Método setResponseBuffering &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)   
 [Miembros SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Clase SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
