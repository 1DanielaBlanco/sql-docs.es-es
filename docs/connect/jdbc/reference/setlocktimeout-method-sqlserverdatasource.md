---
title: "Método setLockTimeout (SQLServerDataSource) | Documentos de Microsoft"
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
apiname: SQLServerDataSource.setLockTimeout
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 10dca5aa-1851-4326-9ae9-7a8430d12d11
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 187db9b99992f2d84e31cbe5ef9c21c4f8d26db3
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="setlocktimeout-method-sqlserverdatasource"></a>Método setLockTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Establece una **int** valor que indica el número de milisegundos que transcurrirán antes de que la base de datos notifique un tiempo de espera de bloqueo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public void setLockTimeout(int lockTimeout)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *lockTimeout*  
  
 Un **int** valor que contiene el número de milisegundos de espera.  
  
## <a name="remarks"></a>Comentarios  
 El tiempo de espera de bloqueo es el número de milisegundos que hay que esperar antes de que la base de datos informe del tiempo de espera para la exclusión. El valor predeterminado de -1 indica que la espera será indefinida. Si se especifica, este valor será el valor predeterminado para todas las instrucciones de la conexión.  
  
> [!NOTE]  
>  Un valor de 0 indica que el tiempo de espera será nulo. Si no se establece la propiedad lockTimeout, el [getLockTimeout](../../../connect/jdbc/reference/getlocktimeout-method-sqlserverdatasource.md) método devuelve el valor predeterminado de -1.  
  
## <a name="see-also"></a>Vea también  
 [Miembros SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Clase SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
