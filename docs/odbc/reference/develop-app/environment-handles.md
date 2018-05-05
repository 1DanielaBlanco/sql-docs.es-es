---
title: Identificadores de entorno | Documentos de Microsoft
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
- environment handles [ODBC]
- handles [ODBC], environment
ms.assetid: 917f1b0c-272b-4e37-a1f5-87cd24b9fa21
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a84e7d5939eb4d4c57b7f59db6d719627cf4be3b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="environment-handles"></a>Identificadores de entorno
Un *entorno* es un contexto global en el que se va a obtener acceso a datos; asociado a un entorno es toda la información que es global por naturaleza, como:  
  
-   Estado del entorno  
  
-   Los diagnósticos de nivel del entorno actuales  
  
-   Los identificadores de conexiones actualmente asignados en el entorno  
  
-   La configuración actual de cada atributo de entorno  
  
 Dentro de un fragmento de código que implementa ODBC (el Administrador de controladores o un controlador), un identificador de entorno identifica una estructura para que contenga esta información.  
  
 Identificadores de entorno no se usan con frecuencia en aplicaciones de ODBC. Siempre se utilizan en las llamadas a **SQLDataSources** y **SQLDrivers** y a veces se usan en las llamadas a **SQLAllocHandle**, **SQLEndTran**, **SQLFreeHandle**, **SQLGetDiagField**, y **SQLGetDiagRec**.  
  
 Cada fragmento de código que implementa ODBC (el Administrador de controladores o un controlador) contiene uno o varios identificadores de entorno. Por ejemplo, el Administrador de controladores mantiene un identificador de entorno independiente para cada aplicación que está conectado a ella. Se asignan a identificadores de entorno **SQLAllocHandle** y liberado con **SQLFreeHandle**.
