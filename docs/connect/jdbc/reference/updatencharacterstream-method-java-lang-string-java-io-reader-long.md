---
title: updateNCharacterStream método String - lector - largo) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: db0a96a8-248f-4664-9c13-f480f309ab91
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 35b39fda419644e0c9d7c424d3909dddac91fff4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32851320"
---
# <a name="updatencharacterstream-method-javalangstring-javaioreader-long"></a>Método updateNCharacterStream (java.lang.String, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Actualiza la columna designada con un valor de flujo de caracteres, que tendrá el número de bytes especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public void updateNCharacterStream(java.lang.String columnLabel,  
                                    java.io.Reader reader,  
                                    long length)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *columnLabel*  
  
 A **cadena** que contiene la etiqueta de columna.  
  
 *lector*  
  
 Un objeto de lector.  
  
 *length*  
  
 Longitud del flujo.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método updateNCharacterStream especificado por el método updateNCharacterStream en la interfaz java.sql.ResultSet.  
  
 Este método pasa los caracteres Unicode de un objeto de lector que seleccione **nchar**, **nvarchar (max)**, **ntext**, y **xml** columnas. Si se utiliza este método en otras columnas de tipo de datos, se producirá una excepción.  
  
 Si la longitud de la secuencia es diferente de lo especificado en el *longitud* parámetro, el controlador JDBC produce una excepción cuando se actualiza o inserta la fila.  
  
 Si la longitud de la secuencia es desconocida, el *longitud* parámetro puede establecerse en -1 para indicar que el controlador debería aceptar el flujo independientemente de su longitud. Con sqljdbc4.jar, recomendamos que utilice el método de JDBC 4.0 [método updateNCharacterStream &#40;java.lang.String, java.io.Reader&#41; ](../../../connect/jdbc/reference/updatencharacterstream-method-java-lang-string-java-io-reader.md) cuando la aplicación desee actualizar la columna de un flujo cuya longitud es desconocido.  
  
## <a name="see-also"></a>Vea también  
 [Método updateNCharacterStream &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md)   
 [Miembros SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Clase SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
