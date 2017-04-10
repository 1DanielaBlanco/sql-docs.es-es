---
title: "c2 audit mode (opci&#243;n de configuraci&#243;n del servidor) | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "auditoría [SQL Server]"
  - "auditorías [SQL Server], opción modo auditoría C2"
  - "auditoría C2"
  - "modo auditoría C2, opción"
  - "registrar intentos"
ms.assetid: 5a8d73a6-c4f6-4967-ba11-ecbcfc90b9cc
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# c2 audit mode (opci&#243;n de configuraci&#243;n del servidor)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  El modo auditoría C2 puede configurarse mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o con la opción **Modo auditoría C2** de **sp_configure**. Al seleccionar esta opción, el servidor registrará tanto los intentos sin éxito como los intentos con éxito de acceso a instrucciones y objetos. Esta información puede servirle de ayuda para perfilar la actividad del sistema y realizar un seguimiento de las posibles infracciones de las directivas de seguridad.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] El estándar de seguridad C2 se ha sustituido por Common Criteria Certification. Vea [common criteria compliance enabled (opción de configuración del servidor)](../../database-engine/configure-windows/common-criteria-compliance-enabled-server-configuration-option.md).  
  
## Archivo de registro de auditoría  
 Los datos del modo auditoría C2 se guardan en un archivo en el directorio de datos predeterminado de la instancia. Si el tamaño del archivo de registro de auditoría supera el límite de 200 megabytes (MB), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creará un archivo nuevo, cerrará el antiguo y escribirá todos los registros de auditoría nuevos en el nuevo archivo. Este proceso continuará hasta que el directorio de datos de auditoría se llene o la función de auditoría se desactive. Para determinar el estado de un seguimiento de C2, consulte la vista de catálogo sys.traces.  
  
> [!IMPORTANT]  
>  El modo auditoría C2 guarda una gran cantidad de información de eventos en el archivo de registro, por lo que puede crecer rápidamente. Si el directorio de datos en el que se guardan los registros se queda sin espacio, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se cerrará automáticamente. Si la auditoría se ha configurado para iniciarse automáticamente, deberá reiniciar la instancia con la marca **-f** (que omite la auditoría) o liberar más espacio en disco para el registro de auditoría.  
  
## Permisos  
 Requiere la pertenencia al rol fijo de servidor **sysadmin** .  
  
## Ejemplo  
 El ejemplo siguiente activa el modo auditoría C2.  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
sp_configure 'c2 audit mode', 1 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
## Vea también  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Opciones de configuración de servidor &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  