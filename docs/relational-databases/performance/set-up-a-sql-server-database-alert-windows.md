---
title: Configurar una alerta de base de datos de SQL Server (Windows) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- alerts [SQL Server], creating
ms.assetid: 65d2c5c1-921f-4eff-9ef7-149170ab61e8
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8eabe827b89c3931523bda848e01471853cbde6b
ms.contentlocale: es-es
ms.lasthandoff: 06/22/2017

---
# <a name="set-up-a-sql-server-database-alert-windows"></a>Configurar una alerta de base de datos (Windows)
  Mediante el Monitor de sistema, puede crear una alerta que se active cuando se alcance un valor de umbral de un contador del Monitor de sistema. Como respuesta a la alerta, el Monitor del sistema puede iniciar una aplicación, como, por ejemplo, una aplicación personalizada creada para tratar la condición de alerta. Por ejemplo, puede crear una alerta que se active cuando el número de interbloqueos sea superior a un valor específico.  
  
 También se pueden definir alertas mediante Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] y el Agente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Para más información, consulte [Alertas](http://msdn.microsoft.com/library/3f57d0f0-4781-46ec-82cd-b751dc5affef).  
  
### <a name="to-set-up-a-sql-server-database-alert"></a>Para configurar una alerta de base de datos de SQL Server  
  
1.  En el árbol de navegación de la ventana Rendimiento, expanda **Registros y alertas de rendimiento**.  
  
2.  Haga clic con el botón derecho en **Alertas**y, después, haga clic en **Nueva configuración de alerta**.  
  
3.  En el cuadro de diálogo **Nueva configuración de alerta** , escriba el nombre de la nueva alerta y, a continuación, haga clic en **Aceptar**.  
  
4.  En la pestaña **General** del cuadro de diálogo de la nueva alerta, agregue un **Comentario**y haga clic en **Agregar** para agregar un contador a la alerta.  
  
     Todas las alertas deben tener, como mínimo, un contador.  
  
5.  En el cuadro de diálogo Agregar contadores, seleccione un objeto de SQL Server de la lista **Objeto de rendimiento** y, a continuación, seleccione un contador en **Seleccionar contadores de la lista**.  
  
6.  Para agregar el contador a la alerta, haga clic en **Agregar**. Puede continuar agregando contadores o hacer clic en **Cerrar** para volver al cuadro de diálogo de la nueva alerta.  
  
7.  En el cuadro de diálogo de la nueva alerta, haga clic en **Superio a** o **Inferior a**in the **Alertar cuando el valor sea** y escriba un valor de umbral en **Límite**.  
  
     La alerta se genera cuando el valor del contador es superior o inferior al valor de umbral, dependiendo de si ha elegido **Superior a** o **Inferior a**.  
  
8.  En los cuadros **Tomar datos de muestra cada** , establezca la frecuencia de muestreo.  
  
9. En la pestaña **Acción** , establezca las acciones que tendrán lugar cada vez que se desencadene la alerta.  
  
10. En la pestaña **Programación** , establezca el programa de inicio y fin de detección de alertas.  
  
## <a name="see-also"></a>Vea también  
 [Crear una alerta de base de datos de SQL Server](../../relational-databases/performance-monitor/create-a-sql-server-database-alert.md)  
  
  
