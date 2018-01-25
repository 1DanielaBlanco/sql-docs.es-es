---
title: "Propiedades de la base de datos (página ChangeTracking) | Microsoft Docs"
ms.custom: 
ms.date: 01/07/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: databases
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.databaseproperties.changetracking.f1
ms.assetid: 9b929640-bc62-449b-9b06-b5a77b8cf372
caps.latest.revision: "13"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 861761574f6ff2b4e803bf64a9c929642dfddf6a
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/18/2018
---
# <a name="database-properties-changetracking-page"></a>Propiedades de la base de datos (página ChangeTracking)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] Utilice esta página para ver o modificar la configuración del seguimiento de cambios de la base de datos seleccionada. Para obtener más información sobre las opciones disponibles en esta página, vea [Habilitar y deshabilitar el seguimiento de cambios &#40;SQL Server&#41;](../../relational-databases/track-changes/enable-and-disable-change-tracking-sql-server.md).  
  
## <a name="options"></a>.  
 **Seguimiento de los cambios**  
 Utilice esta opción para habilitar o deshabilitar el seguimiento de cambios de la base de datos.  
  
 Para habilitar el seguimiento de cambios, debe tener el permiso para modificar la base de datos.  
  
 Al cambiar el valor a **True** , se establece una opción de base de datos que permite habilitar el seguimiento en tablas individuales.  
  
 También puede configurar el seguimiento de cambios utilizando [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md).  
  
 **Período de retención**  
 Especifica el período mínimo para mantener la información de seguimiento de cambios en la base de datos. Los datos se quitarán solo si el valor **Auto Clean-Up** es **True**.  
  
 El valor predeterminado es 2.  
  
 **Unidades del período de retención**  
 Especifica las unidades para el valor del Período de retención. Puede seleccionar **Días**, **Horas**o **Minutos**. El valor predeterminado es **Días**.  
  
 El período de retención mínimo es de 1 minuto. No hay ningún período de retención máximo.  
  
 **Limpieza automática**  
 Indica si los datos del seguimiento de cambios se quitan automáticamente después del período de retención especificado.  
  
 Al habilitar la opción **Limpieza automática** , se restablece cualquier período de retención anterior personalizado al valor predeterminado de 2 días.  
  
## <a name="see-also"></a>Ver también  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE &#40;Transact-SQL de SQL Server&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)  
  
  
