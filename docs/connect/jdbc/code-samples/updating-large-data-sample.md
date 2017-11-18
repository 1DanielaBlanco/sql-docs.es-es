---
title: "Actualizar datos de gran tamaño ejemplo | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76ecc05f-a77d-40a2-bab9-91a7fcf17347
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8df6738cb6913261bebfd5ea469a483328c6678b
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="updating-large-data-sample"></a>Actualizar un ejemplo de datos grandes
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Esto [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] aplicación de ejemplo muestra cómo actualizar una columna grande en una base de datos.  
  
 El archivo de código para este ejemplo se llama updateLargeData.java y se encuentra en la siguiente ubicación:  
  
 \<*directorio de instalación de*> \sqljdbc_\<*versión*>\\<*lenguaje*> \samples\adaptive  
  
## <a name="requirements"></a>Requisitos  
 Para ejecutar esta aplicación de ejemplo, necesitará acceso a la [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] base de datos de ejemplo. También deberá establecer la ruta de clase para incluir el archivo sqljdbc4.jar. Si en la ruta de clase falta una entrada para sqljdbc4.jar, la aplicación de ejemplo produce la excepción común "Clase no encontrada". Para obtener más información sobre cómo establecer la ruta de clase, consulte [con el controlador JDBC](../../../connect/jdbc/using-the-jdbc-driver.md).  
  
> [!NOTE]  
>  El [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] proporciona los archivos de biblioteca de clases sqljdbc.jar, sqljdbc4.jar, sqljdbc41.jar o sqljdbc42.jar que se usan según su configuración preferida de Java Runtime Environment (JRE). Este ejemplo se utiliza la [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) y [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) métodos, que se presentan en la API de JDBC 4.0, para tener acceso a los métodos del búfer de respuestas específicas del controlador. Para compilar y ejecutar este ejemplo, necesitará la biblioteca de clases sqljdbc4.jar, que proporciona compatibilidad con JDBC 4.0. Para obtener más información acerca de qué archivo JAR para elegir, consulte [requisitos del sistema para el controlador JDBC](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, el código de ejemplo realiza una conexión a la [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] base de datos. A continuación, el código de ejemplo crea un objeto de instrucción y usa el [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) método para comprobar si el objeto de instrucción es un contenedor para el elemento especificado [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) clase. El [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) método se usa para tener acceso a los métodos del búfer de respuestas específicas del controlador.  
  
 A continuación, el código de ejemplo establece el modo como el almacenamiento en búfer de respuesta "**adaptable**" mediante el uso de la [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) método de la [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) clase y también se muestra cómo obtener el modo de almacenamiento en búfer adaptable.  
  
 A continuación, se ejecuta la instrucción SQL y coloca los datos que devuelve en una actualizable [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objeto.  
  
 Finalmente, el código muestra recorre en iteración las filas de datos que están contenidas en el conjunto de resultados. Si encuentra un documento vacío resumen, usa la combinación de [updateString](../../../connect/jdbc/reference/updatestring-method-sqlserverresultset.md) y [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) métodos para actualizar la fila de datos y vuelve a almacenar en la base de datos. Si ya hay datos, utiliza el [getString](../../../connect/jdbc/reference/getstring-method-sqlserverresultset.md) método para mostrar algunos de los datos que contiene.  
  
 El comportamiento predeterminado del controlador es "**adaptable.**" Sin embargo, para los conjuntos de resultados adaptables de solo avance y cuando los datos del conjunto de resultados están mayores que la memoria de la aplicación, la aplicación tiene que establecer el modo de almacenamiento en búfer adaptable explícitamente mediante la [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) método de la [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) clase.  
  
 [!code[JDBC#UsingAdaptiveBuffering3](../../../connect/jdbc/codesnippet/Java/updating-large-data-sample_1.java)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con datos de gran tamaño](../../../connect/jdbc/working-with-large-data.md)  
  
  

