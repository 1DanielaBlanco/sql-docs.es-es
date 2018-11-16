---
title: Opción Cancel (herramienta de administración de Distributed Replay) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: fea376de-307a-4b45-b7e2-37df88f3681a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 93aa54bc208980b495aac1b2b33fe11e3472d50e
ms.sourcegitcommit: 0f7cf9b7ab23df15624d27c129ab3a539e8b6457
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51291071"
---
# <a name="cancel-option-distributed-replay-administration-tool"></a>Opción cancel (herramienta de administración de Distributed Replay)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  La herramienta de administración de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay, **DReplay.exe**, es una herramienta de línea de comandos que puede usar para comunicarse con el controlador de reproducción distribuida. En este tema se describe la opción de la línea de comandos **cancel** y la sintaxis correspondiente.  
  
 La opción **cancel** cancela la operación actual que se ejecuta en la controladora.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") Para obtener más información sobre las convenciones de sintaxis que se usan con la sintaxis de la herramienta de administración, vea [Convenciones de sintaxis de Transact-SQL &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
dreplay cancel [-m controller] [-q]   
```  
  
#### <a name="parameters"></a>Parámetros  
 **-m** *controller*  
 Nombre del equipo del controlador. Puede utilizar "`localhost`" o "`.`" para hacer referencia al equipo local.  
  
 Si no se especifica el parámetro **-m** , se usará el equipo local.  
  
 **-q**  
 Modo silencioso. No solicita confirmación.  
  
 El parámetro **-q** es opcional.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se envía una solicitud de cancelación en modo silencioso. El valor `localhost` indica que el servicio del controlador se está ejecutando en el mismo equipo que la herramienta de administración.  
  
```  
dreplay cancel –m localhost -q  
```  
  
## <a name="permissions"></a>Permisos  
 Debe ejecutar la herramienta de administración como un usuario interactivo, como un usuario local o una cuenta de usuario de dominio. Para utilizar una cuenta de usuario local, la herramienta de administración y el controlador se deben estar ejecutando en el mismo equipo.  
  
 Para más información, consulte [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).  
  
## <a name="see-also"></a>Ver también  
 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)  
  
  
