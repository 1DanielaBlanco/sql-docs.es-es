---
title: "Método setPortNumber (SQLServerDataSource) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.setPortNumber
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 59c5fa23-bc1a-4142-af17-70e275f0b833
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 26f5f9e97d086e64f008c7f4af2913a5305585a1
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="setportnumber-method-sqlserverdatasource"></a>Método setPortNumber (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Establece el número de puerto que se usará para comunicarse con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public void setPortNumber(int portNumber)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *númeroDePuerto*  
  
 Un **int** valor que contiene el número de puerto.  
  
## <a name="remarks"></a>Comentarios  
 El número de puerto es el número de puerto TCP/IP que se utiliza al abrir una conexión de socket a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Si no se establece la propiedad portNumber, el [getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md) método devuelve el valor predeterminado de 1433.  
  
> [!NOTE]  
>  El método setPortNumber no hace ninguna comprobación en el valor del puerto pasado del intervalo. Puede pasar un número de puerto que no es válido, como 99999, sin que se desencadene un error.  
  
## <a name="see-also"></a>Vea también  
 [Miembros SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Clase SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
