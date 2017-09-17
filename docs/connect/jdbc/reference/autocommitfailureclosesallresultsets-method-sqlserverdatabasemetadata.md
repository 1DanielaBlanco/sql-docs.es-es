---
title: Cierre del controlador JDBC conjuntos de resultados abiertos | Documentos de Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1739ecb5-e5cb-4807-b5a8-97c0299929d0
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2f2f09f2eacf96ccebb88376ba3866d4188b377d
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# Método autoCommitFailureClosesAllResultSets (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica si el controlador JDBC cierra todos los conjuntos de resultados abiertos, incluso los que se pueden retener, cuando se habilita la confirmación automática y se produce una excepción.  
  
## Sintaxis  
  
```  
  
public boolean autoCommitFailureClosesAllResultSets()  
```  
  
## Valor devuelto  
 **True** si todos los abiertos producir conjuntos, incluso los que se pueden alojar, están cerrados cuando una confirmación automática está habilitada y se produce una excepción. De lo contrario, se devuelve el valor **False**.  
  
## Excepciones  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## Comentarios  
 Este método autoCommitFailureClosesAllResultSets especificado por el método autoCommitFailureClosesAllResultSets en la interfaz java.sql.DatabaseMetaData.  
  
## Vea también  
 [Métodos SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Miembros de SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Clase SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

