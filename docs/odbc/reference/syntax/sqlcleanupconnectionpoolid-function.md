---
title: Función SQLCleanupConnectionPoolID | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLCleanupConnectionPoolID function [ODBC]
ms.assetid: 1fc61908-e003-4587-b91a-32f40569fb99
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b417ddc7b2aedcf2c23e2f607ceb53ee7ffb4c6b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="sqlcleanupconnectionpoolid-function"></a>SQLCleanupConnectionPoolID (función)
**Conformidad**  
 Versión introdujo: ODBC 3,81 normativas: ODBC  
  
 **Resumen**  
 **SQLCleanupConnectionPoolID** informa a un controlador que se agotó un Id. de grupo. Un grupo de identificador puede tiempo de espera siempre que todas las conexiones en un grupo asociado con ese identificador de grupo estaban agotó el tiempo de espera. Vea [agrupación en Microsoft Data Access Components](http://msdn.microsoft.com/library/ms810829.aspx) para obtener más información sobre el tiempo de espera de conexión.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
SQLRETURN  SQLCleanupConnectionPoolID (  
                SQLHENV    EnvironmentHandle  
                SQLPOOLID  PoolID );  
```  
  
## <a name="arguments"></a>Argumentos  
 *EnvironmentHandle*  
 [Entrada] El identificador del entorno del grupo.  
  
 *PoolID*  
 [Entrada] El grupo asociado al identificador de grupo que ha superado el tiempo de espera.  
  
## <a name="returns"></a>Devuelve  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnósticos  
 El Administrador de controladores no se procese la información de diagnóstico que devuelve **SQLCleanupConnectionPoolID**.  
  
 Una aplicación no puede recibir el mensaje de error devuelto por el controlador.  
  
## <a name="remarks"></a>Comentarios  
 **SQLCleanupConnectionPoolID** se puede llamar en cualquier momento, pero el Administrador de controladores garantiza que ningún otro subproceso llama al mismo tiempo **SQLGetPoolID** y ningún otro subproceso está llamando al mismo tiempo  **SQLRateConnection** y **SQLPoolConnect** con un símbolo (token) de información de conexión asignado con ese identificador de grupo. Por lo tanto, el controlador debe asegurarse de que esta función es segura para subprocesos.  
  
 Un controlador puede limpiar los recursos asociados con el identificador de grupo.  
  
 Las aplicaciones no deben llamar directamente a esta función. Un controlador ODBC que admite la agrupación de conexiones dependientes del controlador debe implementar esta función.  
  
 Incluir sqlspi.h para el desarrollo del controlador ODBC.  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar un controlador ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Agrupación de conexiones dependientes del controlador](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Desarrollar el conocimiento de la agrupación de conexiones en un controlador ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
