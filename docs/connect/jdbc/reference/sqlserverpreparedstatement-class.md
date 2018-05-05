---
title: Clase SQLServerPreparedStatement | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a8481c06-fbba-432b-8c69-4f4619c20ad4
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6c7b37e26faedf7cb064880d68e17f4688bfbe73
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="sqlserverpreparedstatement-class"></a>Clase SQLServerPreparedStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Representa la implementación básica de la funcionalidad de la instrucción preparada de JDBC.  
  
 **Paquete:** com.microsoft.sqlserver.jdbc  
  
 **Extiende:** SQLServerStatement  
  
 **Implementa:** [ISQLServerPreparedStatement](../../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
public class SQLServerPreparedStatement  
```  
  
## <a name="remarks"></a>Comentarios  
 SQLServerPreparedStatement proporciona métodos que le permiten especificar parámetros como cualquier tipo Java nativo y muchos tipos de objetos de Java. SQLServerPreparedStatement prepara una instrucción con el [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **sp_prepare** procedimiento almacenado y, a continuación, vuelve al identificador de la instrucción devuelta para cada posterior ejecución de la instrucción, normalmente mediante diferentes parámetros proporcionados por el usuario.  
  
 SQLServerPreparedStatement admite el procesamiento por lotes, donde un conjunto de instrucciones preparadas se ejecuta en una sola base de datos, ida y vuelta para mejorar el rendimiento en tiempo de ejecución.  
  
 Esta clase admite la acción de desencapsular para la clase SQLServerPreparedStatement, ISQLServerPreparedStatement, interfaz, la interfaz java.sql.PreparedStatement, las clases e interfaces compatibles con SQLServerStatement para la acción de desencapsular. Para obtener más información, consulte [contenedores e Interfaces](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Vea también  
 [Miembros de SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Referencia de API del controlador JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
