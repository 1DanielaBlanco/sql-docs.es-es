---
title: "Usar una instrucción SQL sin parámetros | Documentos de Microsoft"
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
ms.assetid: 4b0728bd-059b-4b71-895c-999335bc7427
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 16983e560714bdfb7046da72b04bc4f57f506df5
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2017
---
# <a name="using-an-sql-statement-with-no-parameters"></a>Usar una instrucción SQL sin parámetros
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Para trabajar con datos en un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de datos mediante una instrucción SQL que no contiene ningún parámetro, puede utilizar el [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) método de la [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) clase para devolver un [ SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) que contendrá los datos solicitados. Para ello, primero debe crear un objeto SQLServerStatement mediante el uso de la [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) método de la [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) clase.  
  
 En el ejemplo siguiente, una conexión abierta a la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] base de datos de ejemplo se pasa a la función, se genera y ejecuta una instrucción SQL y, a continuación, se leen los resultados del conjunto de resultados.  
  
 [!code[JDBC#UsingSQLWithNoParams1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-w_0_1.java)]  
  
 Para obtener más información sobre el uso de conjuntos de resultados, vea [administrar conjuntos de resultados con el controlador JDBC](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md).  
  
## <a name="see-also"></a>Vea también  
 [Usar instrucciones con SQL](../../connect/jdbc/using-statements-with-sql.md)  
  
  
