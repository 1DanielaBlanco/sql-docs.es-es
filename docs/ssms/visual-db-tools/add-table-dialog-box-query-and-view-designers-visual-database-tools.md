---
title: Cuadro de diálogo Agregar tabla (Diseñadores de consultas y vistas) (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.query.addtable
- vdtsql.chm:65565
ms.assetid: fce7adcc-4cf5-4a52-9203-11c13d1ecf08
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 809905693c69802a2aa82f4ab6a9fe0177c43c38
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "33047302"
---
# <a name="add-table-dialog-box-query-and-view-designers-visual-database-tools"></a>Agregar tabla (cuadro de diálogo, Diseñadores de consultas y vistas, Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Este cuadro de diálogo permite agregar tablas, vistas, funciones definidas por el usuario o sinónimos a una consulta o una vista.  
  
> [!NOTE]  
> Si se publica la tabla para la replicación, debe modificar el esquema mediante la instrucción Transact-SQL [ALTER TABLE](http://msdn.microsoft.com/en-us/f1745145-182d-4301-a334-18f799d361d1) u Objetos de administración de SQL Server (SMO). Si se modifica el esquema mediante el Diseñador de tablas o el Diseñador de diagramas de base de datos, se intentará eliminar la tabla y volver a crearla. No se pueden eliminar objetos publicados, por lo que la modificación del esquema generará un error.  
  
## <a name="options"></a>Opciones  
**Tablas**  
Muestra las tablas que puede agregar al panel **Diagrama** . Para agregar una tabla, selecciónela y haga clic en **Agregar**. Para agregar varias tablas al mismo tiempo, selecciónelas y haga clic en **Agregar**.  
  
**Vistas**  
Muestra las vistas que puede agregar al panel **Diagrama** . Para agregar una vista, selecciónela y haga clic en **Agregar**. Para agregar varias vistas al mismo tiempo, selecciónelas y haga clic en **Agregar**.  
  
**Funciones**  
Muestra las funciones definidas por el usuario que puede agregar al panel **Diagrama** . Para agregar una función, selecciónela y haga clic en **Agregar**. Para agregar varias funciones al mismo tiempo, selecciónelas y haga clic en **Agregar**.  
  
**Sinónimos**  
Muestra los sinónimos que se pueden agregar al panel **Diagrama** . Para agregar un sinónimo, selecciónelo y haga clic en **Agregar**. Para agregar varios sinónimos al mismo tiempo, selecciónelos y haga clic en **Agregar**.  
  
**Actualizar**  
Actualiza la lista para que incluya los cambios realizados en la base de datos desde la última vez que se recuperó la lista.  
  
**Agregar**  
Agrega los elementos seleccionados.  
  
## <a name="see-also"></a>Ver también  
[Temas de procedimientos de diseño de consultas y vistas &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
