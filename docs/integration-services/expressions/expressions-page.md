---
title: "Página expresiones | Documentos de Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: expressions
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.expressionspage.f1
helpviewer_keywords:
- Expressions Page dialog box
ms.assetid: c9016ec6-11c1-4ebd-b2a7-0fa6631fd9e4
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2517f3b049261614a219d64698a99bd82e14915d
ms.contentlocale: es-es
ms.lasthandoff: 08/03/2017

---
# <a name="expressions-page"></a>Página Expresiones
  Utilice la página **Expresiones** para editar expresiones de propiedad y obtener acceso a los cuadros de diálogo **Editor de expresiones de propiedad** y **Generador de expresiones** .  
  
 Las expresiones de propiedad actualizan los valores de las propiedades cuando se ejecuta el paquete. Se pueden utilizar expresiones de propiedad con las propiedades de paquetes, tareas, contenedores, administradores de conexión y algunos componentes de flujo de datos. Las expresiones se evalúan y se usan los resultados en lugar de los valores en los que se han establecido las propiedades al configurar el paquete y los objetos de paquete. Las expresiones pueden incluir variables y las funciones y los operadores que proporciona el lenguaje de expresiones. Por ejemplo, se puede generar la línea de asunto de la tarea Enviar correo mediante la concatenación del valor de una variable que contenga la cadena "Pronóstico meteorológico para" y los resultados devueltos de la función GETDATE() para crear la cadena "Pronóstico meteorológico para 5/4/2006".  
  
 Para obtener más información sobre cómo se escriben las expresiones y cómo se usan las expresiones de propiedad, vea [Expresiones de Integration Services &#40;SSIS&#41;](../../integration-services/expressions/integration-services-ssis-expressions.md) y [Usar expresiones de propiedad en paquetes](../../integration-services/expressions/use-property-expressions-in-packages.md).  
  
## <a name="options"></a>Opciones  
 **Expresiones (...)**  
 Haga clic en los puntos suspensivos para abrir el cuadro de diálogo **Editor de expresiones de propiedad** . Para más información, consulte [Property Expressions Editor](../../integration-services/expressions/property-expressions-editor.md).  
  
 **\<nombre de propiedad >**  
 Haga clic en los puntos suspensivos para abrir el cuadro de diálogo **Generador de expresiones** . Para más información, consulte [Expression Builder](../../integration-services/expressions/expression-builder.md).  
  
## <a name="see-also"></a>Vea también  
 [Variables de Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md)   
 [Variables del sistema](../../integration-services/system-variables.md)   
 [Integration Services &#40; SSIS &#41; Expresiones](../../integration-services/expressions/integration-services-ssis-expressions.md)  
  
  

