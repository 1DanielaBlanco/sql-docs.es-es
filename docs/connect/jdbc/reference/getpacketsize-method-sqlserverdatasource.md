---
title: Método getPacketSize (SQLServerDataSource) | Documentos de Microsoft
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
- SQLServerDataSource.getPacketSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b2e9f01a-2e51-47e5-90bf-43c62d1be74d
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d4350bb6f3d6213548b298b45052ca009e8f99cd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="getpacketsize-method-sqlserverdatasource"></a>Método getPacketSize (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Devuelve el tamaño de paquete de red actual que se utiliza para comunicarse con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], especificado en bytes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public int getPacketSize()  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un **int** valor que contiene el tamaño de paquete de red actual.  
  
## <a name="remarks"></a>Comentarios  
 Si no se establece la propiedad packetSize, el método getPacketSize devuelve el valor predeterminado de 8000.  
  
## <a name="see-also"></a>Vea también  
 [Miembros SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Clase SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
