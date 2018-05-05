---
title: Compatibilidad con transacciones | Documentos de Microsoft
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
- transactions [ODBC], degree of support
ms.assetid: d56e1458-8da2-4d73-a777-09e045c30a33
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2f3e62cd93f3823a2205ed2c2721ed95749f7a1a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="transaction-support"></a>Compatibilidad con transacciones
El grado de compatibilidad con transacciones es definido por el controlador. ODBC está diseñado para que se implementen en una base de datos de usuario único o de escritorio que no tiene necesidad de administrar varias actualizaciones para sus datos. Además, algunas bases de datos que admiten transacciones realizar solamente para las instrucciones de lenguaje de manipulación de datos (DML) de SQL; hay restricciones o semántica de transacción especiales con respecto al uso del lenguaje de definición de datos (DDL) cuando una transacción está activa. Es decir, puede haber compatibilidad con transacciones actualizaciones simultáneas de varias tablas, pero no para cambiar el número y la definición de tablas durante una transacción.  
  
 Una aplicación determina si se admiten las transacciones, si DDL puede incluirse en una transacción y sus posibles efectos especiales de inclusión de DDL en una transacción, mediante una llamada a **SQLGetInfo** con la opción SQL_TXN_CAPABLE. Para obtener más información, consulte el [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) descripción de la función.  
  
 Si el controlador no admite transacciones, pero la aplicación tiene la capacidad de (mediante una API que no sea ODBC) para bloquear y desbloquear datos, aplicaciones pueden lograr la compatibilidad con transacciones registros de bloqueos y desbloqueo y las tablas según sea necesario. Para implementar el ejemplo de transferencia de la cuenta, la aplicación podría bloquear los registros para ambas cuentas, copie los valores actuales, la primera cuenta de débito, la segunda cuenta de crédito y desbloquear los registros. Si se produce un error en todos los pasos, la aplicación podría restablecer las cuentas con las copias.  
  
 Orígenes de datos aunque admiten transacciones no puede admitir más de una transacción a la vez dentro de un entorno determinado. Aplicaciones llaman a **SQLGetInfo** con la opción SQL_MULTIPLE_ACTIVE_TXN para determinar si un origen de datos puede admitir las transacciones activas simultáneas en más de una conexión en el mismo entorno. Ya hay una transacción por conexión, esto solo es adecuada para las aplicaciones que tienen varias conexiones con el mismo origen de datos.
