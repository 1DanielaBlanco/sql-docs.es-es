---
title: Método updateNClob (java.lang.String, java.io.Reader) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 87621ca7-e64a-49e2-b9c2-551390adaa26
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e632b4719d0f811dfa29a8f21c5fb7573b34e3e1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="updatenclob-method-javalangstring-javaioreader"></a>Método updateNClob (java.lang.String, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Actualiza la columna designada mediante el Readerobject especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public void updateNClob(java.lang.String columnLabel,  
                        java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *columnLabel*  
  
 A **cadena** que indica la etiqueta de columna.  
  
 *lector*  
  
 Un objeto de lector.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método updateNClob especificado por el método updateNClob en la interfaz java.sql.ResultSet.  
  
 Este método solo se admite en **nvarchar (max)**, **ntext**, y **xml** columnas. Si se utiliza este método en cualquier otro tipo de datos, provocará una excepción.  
  
## <a name="see-also"></a>Vea también  
 [Método updateNClob &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md)   
 [Miembros SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Clase SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
