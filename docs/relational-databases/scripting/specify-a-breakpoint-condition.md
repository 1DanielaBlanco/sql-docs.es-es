---
title: Especificar una condición de punto de interrupción | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpt.condition
helpviewer_keywords:
- Transact-SQL debugger, breakpoint conditions
ms.assetid: b43d8a2b-99a3-4fb7-8848-99c042ea7ef7
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0c69e308ffc45e7518e60950b4711c4b29d64f13
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "43060838"
---
# <a name="specify-a-breakpoint-condition"></a>Especificar una condición de punto de interrupción
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Una condición de punto de interrupción es una expresión de [!INCLUDE[tsql](../../includes/tsql-md.md)] evaluada por el depurador cuando se alcanza el punto de interrupción. Si se satisface la condición y se alcanza el número de llamadas especificado, el depurador interrumpe, o bien, realiza la acción definida para el punto de interrupción.  
  
## <a name="specifying-conditions"></a>Especificar condiciones  
 La expresión especificada debe ser una expresión válida de Transact-SQL que se evalúe como un valor booleano. Para obtener más información, vea [Expresiones &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md).  
  
 Si especifica una condición de punto de interrupción con sintaxis no válida, aparecerá inmediatamente un mensaje de advertencia. Si especifica una condición con sintaxis válida, pero la semántica no es válida, aparecerá un mensaje de advertencia la primera vez que se llegue al punto de interrupción. En cualquier caso, el depurador interrumpe la ejecución cuando se alcanza el punto de interrupción.  
  
#### <a name="to-specify-a-condition"></a>Para especificar una condición  
  
1.  En la ventana del editor, haga clic con el botón derecho en el glifo del punto de interrupción y, después, haga clic en la opción **Condición** del menú contextual.  
  
     -O bien-  
  
     En la ventana **Puntos de interrupción** , haga clic con el botón derecho en el glifo del punto de interrupción y, después, haga clic en la opción **Condición** del menú contextual.  
  
2.  En el cuadro de diálogo **Condición de punto de interrupción** , escriba una expresión booleana válida en el cuadro **Condición** .  
  
3.  Elija **Es true** si desea interrumpir la ejecución cuando la expresión se evalúa como **true**, o elija **Ha cambiado** si desea interrumpir la ejecución cuando el valor de la expresión ha cambiado.  
  
    > [!NOTE]  
    >  El depurador no evalúa la expresión booleana hasta la primera vez que se alcanza el punto de interrupción. Si elige **Ha cambiado**, el depurador no considerará la primera evaluación como cambio, por lo que el depurador no interrumpirá le ejecución en la primera evaluación.  
  
## <a name="see-also"></a>Ver también  
 [Especificar un número de llamadas](../../relational-databases/scripting/specify-a-hit-count.md)   
 [Especificar una acción del punto de interrupción](../../relational-databases/scripting/specify-a-breakpoint-action.md)  
  
  
