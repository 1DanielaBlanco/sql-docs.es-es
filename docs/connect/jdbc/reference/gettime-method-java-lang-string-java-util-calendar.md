---
title: "Método getTime (java.lang.String, java.util.Calendar) | Documentos de Microsoft"
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
apiname: SQLServerCallableStatement.getTime (java.lang.String, java.util.Calendar)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 3d4c67c2-a3c8-4a26-a159-89c5d63fda0b
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f24f1bcc53cb6675d12cfceb206514dadc7c9f9b
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="gettime-method-javalangstring-javautilcalendar"></a>Método getTime (java.lang.String, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera el valor del parámetro designado como un objeto java.sql.Time en el lenguaje de programación según el nombre del parámetro, utilizando el objeto de calendario determinado de Java.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public java.sql.Time getTime(java.lang.String sCol,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *sCol*  
  
 A **cadena** que contiene el nombre del parámetro.  
  
 *CAL*  
  
 Un objeto de calendario.  
  
## <a name="return-value"></a>Valor devuelto  
 Un objeto de tiempo.  
  
## <a name="exceptions"></a>Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Comentarios  
 Este método getTime es especificado por el método getTime en la interfaz java.sql.CallableStatement.  
  
 Vea el gráfico titulado "Conversiones de métodos de captador" en [conversiones de tipos de datos de descripción](../../../connect/jdbc/understanding-data-type-conversions.md) para ver qué [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipos de datos se pueden recuperar con este método.  
  
## <a name="see-also"></a>Vea también  
 [getTime (método) &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/gettime-method-sqlservercallablestatement.md)   
 [Miembros de SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Clase SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
