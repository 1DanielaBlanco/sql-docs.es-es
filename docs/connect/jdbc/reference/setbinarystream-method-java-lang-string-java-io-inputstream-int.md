---
title: Método para introducir larga secuencia - setBinaryStream | Documentos de Microsoft
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
ms.topic: article
apiname:
- SQLServerCallableStatement.setBinaryStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 567297bf-5bec-46ae-8264-29639b9b4a06
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d5d98d1f3bfba81c1d51e02c173975177f6b3713
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="setbinarystream-method--javalangstring-javaioinputstream-int"></a>Método setBinaryStream  (java.lang.String, java.io.InputStream, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Establece el parámetro designado en el flujo de entrada especificado, que tendrá el número de bytes indicado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public void setBinaryStream(java.lang.String parameterName,  
                            java.io.InputStream value,  
                            int length)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *parameterName*  
  
 A **cadena** que contiene el nombre del parámetro.  
  
 *value*  
  
 Un objeto InputStream.  
  
 *length*  
  
 Un **int** que indica la longitud en número de bytes.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método setBinaryStream especificado por el método setBinaryStream en la interfaz java.sql.CallableStatement.  
  
 Si la longitud de la secuencia es diferente de lo especificado en el *longitud* parámetro, el controlador JDBC produce una excepción cuando se actualiza o inserta la fila.  
  
 Si la longitud de la secuencia es desconocida, el *longitud* parámetro puede establecerse en -1 para indicar que el controlador debería aceptar el flujo independientemente de su longitud. Con sqljdbc4.jar, recomendamos que utilice el método de JDBC 4.0 [método setBinaryStream (java.lang.String, java.io.InputStream)](../../../connect/jdbc/reference/setbinarystream-method-java-lang-string-java-io-inputstream.md) cuando la aplicación desee actualizar la columna de un flujo cuya longitud se desconozca.  
  
## <a name="see-also"></a>Vea también  
 [setBinaryStream &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/setbinarystream-sqlservercallablestatement.md)   
 [Miembros SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
