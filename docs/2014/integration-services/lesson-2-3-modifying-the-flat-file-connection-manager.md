---
title: 'Paso 3: Modificar el Administrador de conexiones de archivos planos | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 459e3995-2116-4f15-aaa2-32f26113869c
caps.latest.revision: 20
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: e9fd2bed99316f5863ca2ce132e8fb3c9f23f73c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36108372"
---
# <a name="step-3-modifying-the-flat-file-connection-manager"></a>Paso 3: Modificar el Administrador de conexiones de archivos planos
  En esta tarea, modificará el administrador de conexiones de archivos planos que creó y configuró en la lección 1. Cuando se creó inicialmente, el administrador de conexiones de archivos planos se configuró para cargar de forma estática un único archivo. Para permitir que el Administrador de conexiones de archivos planos cargue archivos de forma iterativa, debe modificar la propiedad ConnectionString del administrador de conexiones de modo que acepte la variable `User:varFileName`, definida por el usuario, que contiene la ruta de acceso del archivo que se cargará en tiempo de ejecución.  
  
 Al modificar el administrador de conexiones para que use la variable definida por el usuario `User::varFileName`para rellenar la propiedad ConnectionString del administrador de conexiones, este podrá conectarse a distintos archivos planos. En tiempo de ejecución, cada iteración del contenedor de bucles Foreach actualizará dinámicamente la variable `User::varFileName` . A su vez, actualizar esta variable da lugar a que el administrador de conexiones se conecte a un archivo plano distinto, y que la tarea de flujo de datos procese un conjunto de datos distinto.  
  
### <a name="to-configure-the-flat-file-connection-manager-to-use-a-variable-for-the-connection-string"></a>Para configurar el Administrador de conexiones de archivos planos de modo que utilice una variable para la cadena de conexión  
  
1.  En el panel **Administradores de conexión** , haga clic con el botón derecho en **Sample Flat File Source Data**y, después, seleccione **Propiedades**.  
  
2.  En la ventana Propiedades, para **Expresiones**, haga clic en la celda vacía y,después, haga clic en el botón de puntos suspensivos **(…)**.  
  
3.  En el **Editor de expresiones de propiedad** cuadro de diálogo, en la **propiedad** columna, escriba o seleccione `ConnectionString`.  
  
4.  En la columna **Expresión** , haga clic en el botón de puntos suspensivos **(…)** para abrir el cuadro de diálogo **Generador de expresiones** .  
  
5.  En el cuadro de diálogo **Generador de expresiones** , expanda el nodo **Variables** .  
  
6.  Arrastre la variable **User::varFileName**hasta el cuadro **Expresión** .  
  
7.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Generador de expresiones** .  
  
8.  Haga clic en **Aceptar** de nuevo para cerrar el cuadro de diálogo **Editor de expresiones de propiedad** .  
  
## <a name="next-lesson-task"></a>Tarea de la siguiente lección  
 [Paso 4: Probar el paquete del tutorial de la lección 2](../integration-services/lesson-2-4-testing-the-lesson-2-tutorial-package.md)  
  
  