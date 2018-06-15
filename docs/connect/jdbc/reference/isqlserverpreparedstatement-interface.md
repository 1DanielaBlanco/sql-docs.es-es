---
title: Interfaz ISQLServerPreparedStatement | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: cf87892e-5c34-4ac6-8258-c2a81e117b26
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ec1e10bc98fe8e1f61c15d97777e1c85a27031e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32839050"
---
# <a name="isqlserverpreparedstatement-interface"></a>Interfaz ISQLServerPreparedStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Representa la implementación básica de la funcionalidad de la instrucción preparada de JDBC. Esta interfaz se agregó en [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] controlador JDBC 3.0.  
  
 **Paquete:** com.microsoft.sqlserver.jdbc  
  
 **Extiende:** java.sql.PreparedStatement, [ISQLServerStatement](../../../connect/jdbc/reference/isqlserverstatement-interface.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public interface ISQLServerPreparedStatement  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se implementa mediante [clase SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).  
  
 Esta interfaz expone los siguientes [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-métodos específicos:  
  
|Método|Para obtener más información, vea|  
|------------|-------------------------------|  
|public void setDateTimeOffset(int, microsoft.sql.DateTimeOffset)|[setDateTimeOffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlserverpreparedstatement.md)|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de API del controlador JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
