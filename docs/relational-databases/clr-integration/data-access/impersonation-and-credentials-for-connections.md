---
title: "Suplantación y las credenciales para conexiones | Documentos de Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: clr
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- impersonation [CLR integration]
- security [CLR integration]
- database objects [CLR integration], connections
- connections [CLR integration]
- authentication [CLR integration]
- user impersonation [CLR integration]
- credentials [CLR integration]
- database objects [CLR integration], security
ms.assetid: 293dce7d-1db2-4657-992f-8c583d6e9ebb
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b3c4495b75f9464eb0e8211eeea6529264053c61
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="impersonation-and-credentials-for-connections"></a>Suplantación y credenciales para conexiones
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]En el [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] integración common language runtime (CLR), mediante la autenticación de Windows es compleja, pero es más segura que usar autenticación de SQL Server. Al usar la autenticación de Windows, tenga presente las consideraciones siguientes.  
  
 De forma predeterminada, un proceso de SQL Server que se conecta a Windows adquiere el contexto de seguridad de la cuenta de servicio de Windows para SQL Server. Pero es posible asignar una función CLR a una identidad del proxy, para que sus conexiones salientes tengan un contexto de seguridad diferente que el de la cuenta del servicio de Windows.  
  
 En algunos casos, puede que desee suplantar al llamador utilizando el **SqlContext.WindowsIdentity** propiedad en lugar de ejecutarse como cuenta de servicio. El **WindowsIdentity** instancia representa la identidad del cliente que invoca el código que realiza la llamada y solo está disponible cuando el cliente utiliza la autenticación de Windows. Después de haber obtenido el **WindowsIdentity** instancia, se puede llamar a **Impersonate** para cambiar el token de seguridad del subproceso y, a continuación, abra Conexiones de ADO.NET en nombre del cliente.  
  
 Después de llamar a SQLContext.WindowsIdentity.Impersonate, no se puede obtener acceso a datos locales y no se puede obtener acceso a datos del sistema. Para tener acceso a datos de nuevo, tendrá que llamar al método WindowsImpersonationContext.Undo.  
  
 En el ejemplo siguiente se muestra cómo suplantar al llamador mediante la **SqlContext.WindowsIdentity** propiedad.  
  
 Visual C#  
  
```  
WindowsIdentity clientId = null;  
WindowsImpersonationContext impersonatedUser = null;  
  
clientId = SqlContext.WindowsIdentity;  
  
// This outer try block is used to protect from   
// exception filter attacks which would prevent  
// the inner finally block from executing and   
// resetting the impersonation.  
try  
{  
   try  
   {  
      impersonatedUser = clientId.Impersonate();  
      if (impersonatedUser != null)  
         return GetFileDetails(directoryPath);  
         else return null;  
   }  
   finally  
   {  
      if (impersonatedUser != null)  
         impersonatedUser.Undo();  
   }  
}  
catch  
{  
   throw;  
}  
```  
  
> [!NOTE]  
>  Para obtener información acerca de los cambios de comportamiento en la suplantación, consulte [cambios recientes en las características del motor de base de datos en SQL Server 2016](../../../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md).  
  
 Además, si obtuvo la instancia de identidad en [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, no puede propagar esa instancia a otro equipo de forma predeterminada; la infraestructura de seguridad de Windows restringe esa acción de forma predeterminada. Sin embargo, hay un mecanismo denominado "delegación" que habilita la propagación de identidades de Windows a través de varios equipos de confianza. Puede aprender más acerca de la delegación en el artículo de TechNet, "[Kerberos Protocol Transition and Constrained Delegation](http://go.microsoft.com/fwlink/?LinkId=50419)".  
  
## <a name="see-also"></a>Vea también  
 [Objeto SqlContext](../../../relational-databases/clr-integration-data-access-in-process-ado-net/sqlcontext-object.md)  
  
  
