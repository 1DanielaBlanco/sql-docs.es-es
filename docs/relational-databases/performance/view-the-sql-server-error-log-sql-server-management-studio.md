---
title: Ver el registro de errores de SQL Server (SQL Server Management Studio) | Microsoft Docs
ms.custom: 
ms.date: 07/29/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- viewing logs
- displaying logs
- errors [SQL Server], logs
- logs [SQL Server], SQL Server error logs
- logs [SQL Server], viewing
ms.assetid: 55f468ba-146c-4ab3-95cd-d35d051afd12
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4acdc87a3317c38b5b19235dae681bce426244e3
ms.contentlocale: es-es
ms.lasthandoff: 06/22/2017

---
# <a name="view-the-sql-server-error-log-sql-server-management-studio"></a>Ver el registro de errores de SQL Server (SQL Server Management Studio)
  El registro de errores de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contiene eventos definidos por el usuario y determinados eventos del sistema que le interesará tener para solucionar problemas. 
  

  ## <a name="how-to-view-the-logs"></a>Cómo ver los registros
1.  En SSMS, seleccione **Explorador de objetos**

>Para **abrir** el Explorador de objetos, el método abreviado de teclado es **F8**. O bien, en el menú superior, haga clic en Ver/Explorador de objeto ![Object_explorer](../../relational-databases/performance/media/object-explorer.png) 


2.  En el **Explorador de objetos**, conéctese a una instancia de SQL Server y expándala.
  
3.  Busque y expanda la sección **Administración** (suponiendo que tiene los permisos para verla).

4.  Haga clic con el botón derecho en **Registros de SQL Server**, seleccione Ver y, luego, elija **Ver registro de SQL Server**.
 ![View_SQLServer_Log_SSMS](../../relational-databases/performance/media/view-sqlserver-log-ssms.png) 
 
5.  Aparecerá el Visor de archivos de registro (esto puede demorar un minuto) con una lista de los registros que puede ver.
  
6. Varias personas han recomendado la publicación [Identify location of the SQL Server Error Log file](https://www.mssqltips.com/) (Identificar la ubicación del archivo de registro de errores de SQL Server) de [MSSQLTips.com](https://www.mssqltips.com/sqlservertip/2506/identify-location-of-the-sql-server-error-log-file/). Ahí puede encontrar gran cantidad de excelente información, no se olvide de revisarlo.
  
  

