---
title: "Validar guías de planes tras una actualización | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-plan-guides
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- plan guides [SQL Server], validating after upgrade
ms.assetid: a55ebd88-6f58-454d-b1c4-991b88add522
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 986538833b7f1b9cc6977449b918997b21828159
ms.lasthandoff: 04/11/2017

---
# <a name="validate-plan-guides-after-upgrade"></a>Validar guías de planes tras una actualización
  Se recomienda volver a evaluar y probar las definiciones de guías de plan al actualizar la aplicación a una nueva versión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Los requisitos de optimización del rendimiento y el comportamiento de la coincidencia de las guías de plan pueden cambiar. Aunque una guía de plan no válida no hará que una consulta provoque un error, el plan se compilada sin utilizar la guía de plan y posiblemente no sea la mejor opción. Después de actualizar una base de datos a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], es recomendable que realice las tareas siguientes:  
  
-   Valide las guías de plan existentes con la función [sys.fn_validate_plan_guide](../../relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql.md) .  
  
-   Utilice eventos extendido para supervisar los planes equivocados durante un cierto período de tiempo con el evento [Guía de plan incorrecta](../../relational-databases/event-classes/plan-guide-unsuccessful-event-class.md) .  
  
  
