---
title: "Método updateBinaryStream (int, java.io.InputStream, int) | Documentos de Microsoft"
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
apiname: SQLServerResultSet.updateBinaryStream (int, java.io.InputStream, int)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: c8e55377-aaea-4415-8159-938fab1b2a93
caps.latest.revision: "21"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eab9c5a4c0bd6b088fa893913d2d78076879b791
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="updatebinarystream-method-int-javaioinputstream-int"></a>Método updateBinaryStream (int, java.io.InputStream, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Actualiza la columna designada con un valor de flujo binario, que tendrá el número especificado de bytes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public void updateBinaryStream(int columnIndex,  
                               java.io.InputStream x,  
                               int length)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *columnIndex*  
  
 Un **int** que indica el índice de columna.  
  
 *x*  
  
 Un objeto InputStream.  
  
 *length*  
  
 Un **int** que indica la longitud de la secuencia.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método updateBinaryStream especificado por el método updateBinaryStream en la interfaz java.sql.ResultSet.  
  
 Este método pasa bytes desde un objeto InputStream que seleccione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] columnas binarias como binary, varbinary, varbinary (max), image, xml y udt. Este método no admite la actualización de columnas de caracteres. Para actualizar las columnas de caracteres con un InputStream, use la [updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md) método.  
  
 Si la longitud de la secuencia es diferente al especificado en el *longitud* parámetro, el controlador JDBC produce una excepción cuando se actualiza o inserta la fila.  
  
 Si la longitud de la secuencia es desconocida, el *longitud* parámetro puede establecerse en -1 para indicar que el controlador debería aceptar el flujo independientemente de su longitud. Con sqljdbc4.jar, recomendamos que utilice el método de JDBC 4.0 [updateBinaryStream método &#40; int, java.io.InputStream &#41;](../../../connect/jdbc/reference/updatebinarystream-method-int-java-io-inputstream.md) cuando la aplicación desee actualizar la columna de un flujo cuya longitud se desconozca.  
  
## <a name="see-also"></a>Vea también  
 [Método updateBinaryStream &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)   
 [Miembros de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Clase SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
