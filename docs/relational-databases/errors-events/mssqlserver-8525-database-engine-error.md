---
title: MSSQLSERVER_8525 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- "8525"
helpviewer_keywords:
- 8525 (Database Engine error)
ms.assetid: 297867c1-691e-4d6b-a3be-a7575015ecfa
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: eb958ba1702796c4e51d459c9de1b1f2c04099fa
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver8525"></a>MSSQLSERVER_8525
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|SQL Server|  
|Identificador del evento|8525|  
|Origen del evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nombre simbólico||  
|Texto del mensaje|Se completó la transacción distribuida. Dé de alta esta sesión en una nueva transacción o en la transacción NULL.|  
  
## <a name="explanation"></a>Explicación  
El modelo de programación para utilizar el Coordinador de transacciones distribuidas con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] exige que las aplicaciones se den de alta y de baja explícitamente en una transacción distribuida.  
  
Este error se produce cuando se cumplen las siguientes condiciones:  
  
-   La aplicación de ha dado de alta en una transacción distribuida.  
  
-   La transacción ha finalizado (se ha confirmado o revertido) por alguna razón.  
  
-   La aplicación de usuario no se ha dado de baja explícitamente de una transacción distribuida o no se ha dado de alta explícitamente en una nueva transacción distribuida.  
  
-   La aplicación intenta realizar una operación transaccional que no es darse de baja de una transacción distribuida existente ni darse de alta en una nueva transacción distribuida, como emitir una consulta o iniciar una transacción local.  
  
El estado de error 1 se utiliza cuando la aplicación realiza una operación que crea transacciones locales y el estado 2 se utiliza cuando la aplicación intenta darse de alta en una sesión enlazada.  
  
## <a name="user-action"></a>Acción del usuario  
Después de que una aplicación se haya dado de alta en una transacción distribuida, la aplicación debe darse de baja explícitamente de la transacción distribuida o darse de alta en otra transacción distribuida. Esto la dará de baja implícitamente de una transacción dada de alta previamente. Para obtener la sintaxis exacta para darse de baja o de alta en una transacción distribuida, vea el manual de la interfaz de programación para la aplicación.  
  
