---
title: Especificar una condición de punto de interrupción | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
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
ms.openlocfilehash: 8ecee19e4846d2ccf49c21d90b8ab9815ed63a5b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37282781"
---
# <a name="specify-a-breakpoint-condition"></a>Especificar una condición de punto de interrupción
  Una condición de punto de interrupción es una expresión de [!INCLUDE[tsql](../../includes/tsql-md.md)] evaluada por el depurador cuando se alcanza el punto de interrupción. Si se satisface la condición y se alcanza el número de llamadas especificado, el depurador interrumpe, o bien, realiza la acción definida para el punto de interrupción.  
  
## <a name="specifying-conditions"></a>Especificar condiciones  
 La expresión especificada debe ser una expresión válida de Transact-SQL que se evalúe como un valor booleano. Para obtener más información, vea [Expresiones &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/expressions-transact-sql).  
  
 Si especifica una condición de punto de interrupción con sintaxis no válida, aparecerá inmediatamente un mensaje de advertencia. Si especifica una condición con sintaxis válida, pero la semántica no es válida, aparecerá un mensaje de advertencia la primera vez que se llegue al punto de interrupción. En cualquier caso, el depurador interrumpe la ejecución cuando se alcanza el punto de interrupción.  
  
#### <a name="to-specify-a-condition"></a>Para especificar una condición  
  
1.  En la ventana del editor, haga clic con el botón derecho en el glifo del punto de interrupción y, después, haga clic en la opción **Condición** del menú contextual.  
  
     -o bien-  
  
     En la ventana **Puntos de interrupción** , haga clic con el botón derecho en el glifo del punto de interrupción y, después, haga clic en la opción **Condición** del menú contextual.  
  
2.  En el cuadro de diálogo **Condición de punto de interrupción** , escriba una expresión booleana válida en el cuadro **Condición** .  
  
3.  Elija **es true** si desea interrumpir cuando la expresión se evalúa como `true`, o elija **ha cambiado** si desea interrumpir cuando el valor de la expresión ha cambiado.  
  
    > [!NOTE]  
    >  El depurador no evalúa la expresión booleana hasta la primera vez que se alcanza el punto de interrupción. Si elige **Ha cambiado**, el depurador no considerará la primera evaluación como cambio, por lo que el depurador no interrumpirá le ejecución en la primera evaluación.  
  
## <a name="see-also"></a>Vea también  
 [Especificar un número de llamadas](specify-a-hit-count.md)   
 [Especificar una acción del punto de interrupción](specify-a-breakpoint-action.md)  
  
  
