---
title: Método getXopenStates (SQLServerDataSource) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDataSource.getXopenStates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: de6fdf6b-8345-4490-b35e-7115b61e782e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5657adea99d7a7ba3e6a5d51ebf39f84cd39de08
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="getxopenstates-method-sqlserverdatasource"></a>Método getXopenStates (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Devuelve un **booleano** valor que indica si está habilitada la conversión de Estados SQL Estados conformes a XOPEN.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public boolean getXopenStates()  
```  
  
## <a name="return-value"></a>Valor devuelto  
 **True** si está habilitada la conversión de Estados SQL Estados conformes a XOPEN. De lo contrario, se devuelve el valor **False**.  
  
## <a name="remarks"></a>Comentarios  
 Si la propiedad xopenStates se establece en **true**, el [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] convertirá Estados SQL a Estados conformes a XOPEN. El valor predeterminado es **false**, lo que hace que el controlador JDBC generar códigos de estado SQL 99. Si no se establece xopenStates, el método getXopenStates devuelve el valor predeterminado de **false**.  
  
## <a name="see-also"></a>Vea también  
 [Miembros SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Clase SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
