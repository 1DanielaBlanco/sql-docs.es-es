---
title: "remote admin connections (opción de configuración del servidor) | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- administrator connections [SQL Server]
- DAC
- connections [SQL Server], dedicated administrator
- remote admin connections option
- dedicated administrator connections [SQL Server]
ms.assetid: bf32b60a-7a48-401f-b6be-b5e2e46c413f
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 9cfa41a838ebb89777b44464ec2b2a48b256c3f9
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="remote-admin-connections-server-configuration-option"></a>remote admin connections (opción de configuración del servidor)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proporciona una conexión de administrador dedicada (DAC). La conexión DAC permite a los administradores tener acceso al servidor en ejecución a fin de realizar funciones de diagnóstico o ejecutar instrucciones [!INCLUDE[tsql](../../includes/tsql-md.md)] , o para solucionar problemas del servidor incluso cuando está bloqueado o se ejecuta en un estado anormal, y no responde a ninguna conexión de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] . De forma predeterminada, la conexión DAC solo está disponible en un cliente del servidor. Para habilitar las aplicaciones cliente en equipos remotos de modo que usen la DAC, utilice la opción remote admin connections de sp_configure.  
  
 De forma predeterminada, la DAC solo escucha en la dirección IP de bucle invertido (127.0.0.1) a través del puerto 1434. Si el puerto TCP 1434 no está disponible, se asigna dinámicamente un puerto TCP al iniciarse [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Cuando haya más de una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instalada en un equipo, compruebe en el registro de errores el número de puerto TCP.  
  
 En la siguiente tabla se muestran los posibles valores para la opción remote admin connections.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|0|Indica que solo se permiten conexiones locales mediante la DAC.|  
|1|Indica que la DAC permite las conexiones remotas.|  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo permite utilizar una DAC desde un equipo remoto.  
  
```  
sp_configure 'remote admin connections', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [Conexión de diagnóstico para administradores de bases de datos](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)  
  
  

