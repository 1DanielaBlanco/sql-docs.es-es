---
title: "Crear grupos de jerarquía recursiva (generador de informes y SSRS) | Documentos de Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b6f587b40c53ff64b484b86a324b92ca5de21b77
ms.contentlocale: es-es
ms.lasthandoff: 08/09/2017

---
# <a name="creating-recursive-hierarchy-groups-report-builder-and-ssrs"></a>Crear grupos de jerarquía recursiva (Generador de informes y SSRS)
Para mostrar datos recursivos en informes paginados de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (donde la relación entre el elemento primario y el elemento secundario se representa con campos del conjunto de datos), establezca la expresión de grupo de región de datos según el campo secundario y establezca la propiedad Parent según el campo primario.  
  
 Un uso habitual de los grupos de jerarquía recursiva es mostrar datos jerárquicos, por ejemplo, los empleados en un organigrama. El conjunto de datos incluye una lista de empleados y jefes, donde los nombres de los jefes también aparecen en la lista de empleados.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="creating-recursive-hierarchies"></a>Crear jerarquías recursivas  
 Para generar una jerarquía recursiva en una región de datos Tablix, establezca la expresión de grupo en el campo que especifica los datos secundarios y la propiedad Parent del grupo en el campo que especifica los datos primarios. Por ejemplo, para un conjunto de datos que contiene campos para identificador de empleado e identificador de administrador, establezca la expresión de grupo en el identificador de empleado y la propiedad Parent en el identificador de administrador.  
  
 Los grupos que se definen como jerarquía recursiva (es decir, los que usan la propiedad Parent) solo pueden tener una expresión de grupo. Puede usar la función **Level** en el margen del cuadro de texto para aplicar sangría a los nombres de los empleados en función de su nivel en la jerarquía.  
  
 Para obtener más información, vea [agregar o eliminar un grupo en una región de datos &#40; El generador de informes y SSRS &#41; ](../../reporting-services/report-design/add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) y [crear un grupo de jerarquía recursiva &#40; El generador de informes y SSRS &#41; ](../../reporting-services/report-design/create-a-recursive-hierarchy-group-report-builder-and-ssrs.md).  
  
### <a name="aggregate-functions-that-support-recursion"></a>Funciones de agregado que admiten recursividad  
 Puede usar funciones de agregado de Reporting Services que aceptan el parámetro *Recursive* para calcular los datos de resumen para una jerarquía recursiva. Las funciones siguientes aceptan **Recursive** como parámetro: [Sum](../../reporting-services/report-design/report-builder-functions-sum-function.md), [Avg](../../reporting-services/report-design/report-builder-functions-avg-function.md), [Count](../../reporting-services/report-design/report-builder-functions-count-function.md), [CountDistinct](../../reporting-services/report-design/report-builder-functions-countdistinct-function.md), [CountRows](../../reporting-services/report-design/report-builder-functions-countrows-function.md), [Max](../../reporting-services/report-design/report-builder-functions-max-function.md), [Min](../../reporting-services/report-design/report-builder-functions-min-function.md), [StDev](../../reporting-services/report-design/report-builder-functions-stdev-function.md), [StDevP](../../reporting-services/report-design/report-builder-functions-stdevp-function.md), [Sum](../../reporting-services/report-design/report-builder-functions-sum-function.md), [Var](../../reporting-services/report-design/report-builder-functions-var-function.md)y [VarP](../../reporting-services/report-design/report-builder-functions-varp-function.md). Para más información, vea [Referencia a las funciones de agregado &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md).  
  
## <a name="see-also"></a>Vea también  
 [Tablas, matrices y listas &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Región de datos Tablix &#40; El generador de informes y SSRS &#41;](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)   
 [Referencia de funciones de agregado &#40; El generador de informes y SSRS &#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md)   
 [Tablas &#40; El generador de informes y SSRS &#41;](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [Matrices &#40; El generador de informes y SSRS &#41;](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)   
 [Listas de &#40; El generador de informes y SSRS &#41;](../../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)    
 [Tablas, Matrices y listas de &#40; El generador de informes y SSRS &#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
