---
title: Método getSelectMethod (SQLServerDataSource) | Documentos de Microsoft
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
- SQLServerDataSource.getSelectMethod
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b6255d2e-0028-474a-afa8-553ef092243e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e68aa63db6b1bc5af9ea046e1501d25c5b1501bb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="getselectmethod-method-sqlserverdatasource"></a>Método getSelectMethod (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Devuelve el tipo de cursor predeterminado usado para todos los conjuntos de resultados que se crean mediante este [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public java.lang.String getSelectMethod()  
```  
  
## <a name="return-value"></a>Valor devuelto  
 A **cadena** valor que contiene el tipo de cursor predeterminado.  
  
## <a name="remarks"></a>Comentarios  
 La propiedad selectMethod especifica el tipo de cursor predeterminado que se utiliza para un conjunto de resultados. Esta propiedad es útil cuando se estén abordando grandes conjuntos de resultados y no se quiera almacenar el conjunto de resultados entero en la memoria del lado cliente. Si se establece la propiedad en "cursor", podrá crear un cursor en el lado del servidor que puede capturar fragmentos más pequeños de cada vez. Si no se establece la propiedad selectMethod, el método getSelectMethod devuelve el valor predeterminado "direct".  
  
## <a name="see-also"></a>Vea también  
 [Miembros SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Clase SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
