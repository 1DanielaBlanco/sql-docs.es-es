---
title: "Método getNClob (int) | Documentos de Microsoft"
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
ms.assetid: 10dfa251-9408-469e-ae2a-1acf3917cf47
caps.latest.revision: "14"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 071655069cbbd0548a513d2377f940467c040883
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="getnclob-method-int"></a>Método getNClob (int) 
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera el valor de JDBC designado **NCLOB** parámetro como un objeto NClob en el lenguaje de programación Java.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public java.sql.NClob getNClob(int parameterIndex)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *parameterIndex*  
  
 Un **int** que indica el índice del parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 ANClobobject.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método getNClob especificado por el método getNClob en la interfaz java.sql.CallableStatement.  
  
 Este método solo admite la recuperación **NCHAR**, **NVARCHAR**, **NTEXT**, y **XML** parámetros. Si estos métodos se llaman en otros parámetros del tipo de datos, se producirá una excepción.  
  
## <a name="see-also"></a>Vea también  
 [Método getNClob &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md)   
 [Miembros SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
