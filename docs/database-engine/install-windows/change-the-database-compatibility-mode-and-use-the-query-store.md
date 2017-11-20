---
title: "Cambiar el modo de compatibilidad de la base de datos y usar el almacén de consultas | Microsoft Docs"
ms.custom: 
ms.date: 07/21/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: sql
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- query plans [SQL Server], migrating
- upgrading SQL Server, migrating query plans
- plan guides [SQL Server], migrating query plans
ms.assetid: 7e02a137-6867-4f6a-a45a-2b02674f7e65
caps.latest.revision: 19
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 514fe566dd9a26d4a6244e8fb067f97678d2dbc7
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="change-the-database-compatibility-mode-and-use-the-query-store"></a>Cambiar el modo de compatibilidad de la base de datos y usar el almacén de consultas
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

En SQL Server 2016 y SQL Server 2017, algunos cambios solo se habilitan una vez que el nivel de DATABASE_COMPATIBILITY de una base de datos se ha cambiado. Esto se realiza por varias razones:  
  
- Ya que la actualización es una operación unidireccional (no se puede degradar el formato de archivo), hay un valor en la separación de la habilitación de características nuevas para una operación independiente dentro de la base de datos.  Es posible revertir un valor a un nivel de DATABASE_COMPATIBILITY anterior.  El nuevo modelo reduce el número de pasos que hay que realizar durante una ventana de interrupción.  
  
- Los cambios en el procesador de consultas pueden tener efectos complejos.  Aun cuando un cambio "bueno" en el sistema puede ser bueno para la mayoría de los clientes, para otros podría ser el causante de una regresión inaceptable en una consulta importante.  Separar esta lógica del proceso de actualización permite que las características, como el almacén de consultas, mitiguen las regresiones de elección del plan rápidamente o incluso las eviten completamente en servidores de producción.  
  
> [!NOTE]  
>  Si el nivel de compatibilidad de una base de datos de usuario era 100 o superior antes de la actualización, permanece igual después de la misma. Si el nivel de compatibilidad era 90 antes de la actualización, en la base de datos actualizada, el nivel de compatibilidad se establece en 100, que es el nivel de compatibilidad mínimo admitido en [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Los niveles de compatibilidad de las bases de datos tempdb, model, msdb y Resource quedan establecidos en el nivel de compatibilidad actual después de la actualización. La base de datos del sistema maestra conserva el nivel de compatibilidad que tenía antes de la actualización. 
  
 El proceso de actualización para habilitar la nueva funcionalidad del procesador de consultas está relacionado con el modelo de servicio posterior a la versión del producto.  Algunas de esas correcciones se publican bajo la marca de seguimiento 4199.  Los clientes que necesitan correcciones pueden participar en esas correcciones sin causar regresiones inesperadas para otros clientes.  El modelo de mantenimiento posterior a la versión para las revisiones del procesador de consultas se documenta [aquí](https://support.microsoft.com/en-us/kb/974006). A partir de SQL Server 2016, moverse a un nuevo nivel de compatibilidad implica que ya no se necesite la marca de seguimiento 4199, porque esas correcciones ya están habilitadas de forma predeterminada en el nivel de compatibilidad más reciente.  Por lo tanto, como parte del proceso de actualización, es importante validar que 4199 no está habilitado una vez que se completa el proceso de actualización.  
  
 El flujo de trabajo recomendado para actualizar el procesador de consultas a la versión más reciente del código es:  
  
1.  Actualizar una base de datos a SQL Server 2016 sin cambiar el nivel de compatibilidad de la base de datos (que se mantenga en el nivel anterior)  
  
2.  Habilitar el almacén de consultas en la base de datos. Para más información sobre cómo habilitar y usar el almacén de consultas, vea [Monitoring Performance By Using the Query Store](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md).  
  
3.  Esperar un tiempo suficiente para recopilar datos representativos de la carga de trabajo.  
  
4.  Cambiar el nivel de compatibilidad de la base de datos al nivel de compatibilidad actual. 

   >[!NOTE]
   >El nivel de compatibilidad más reciente depende de la versión de SQL Server.
   >- SQL Server 2016: 130
   >- SQL Server 2017: 140

5. Con SQL Server Management Studio, evaluar si hay regresiones de rendimiento en consultas específicas tras cambiar el nivel de compatibilidad.
  
6.  Para los casos en los que hay regresiones, forzar el plan anterior en el almacén de consultas.  
  
7.  Si no se pudieron forzar planes de consulta o si el rendimiento sigue siendo insuficiente, considere la posibilidad de revertir el nivel de compatibilidad al valor anterior y, después, póngase en contacto con la asistencia al cliente de Microsoft.  
  
## <a name="see-also"></a>Vea también  
 [Ver o cambiar el nivel de compatibilidad de una base de datos](../../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md)  
  
  

