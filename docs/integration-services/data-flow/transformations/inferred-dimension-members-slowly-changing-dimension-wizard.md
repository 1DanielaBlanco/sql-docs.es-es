---
title: "Miembros de dimensión deducidos (Asistente para dimensiones de variación lenta) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.dts.loaddimwizard.inferrdim.f1
ms.assetid: 809e395f-2e10-48ff-8860-56403f130628
caps.latest.revision: "20"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: be5af4677309346b3aacbe5198547ac5efb5d1ed
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2017
---
# <a name="inferred-dimension-members-slowly-changing-dimension-wizard"></a>Miembros de dimensión deducidos (Asistente para dimensiones variables)
  Utilice el cuadro de diálogo **Miembros de dimensión deducidos** para especificar opciones de la utilización de miembros deducidos. Los miembros deducidos existen cuando una tabla de hechos hace referencia a miembros de dimensión que todavía no se han cargado. Cuando se cargan datos del miembro deducido, se puede actualizar el registro existente en lugar de crear uno nuevo.  
  
 Para obtener más información acerca de este asistente, vea [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Opciones  
 **Habilitar compatibilidad con miembros deducidos**  
 Si decide habilitar el uso de miembros deducidos, debe seleccionar una de las dos opciones siguientes.  
  
 **Todas las columnas con un tipo de cambio son NULL**  
 Especifique si escribe valores NULL en todas las columnas con un tipo de cambio en el nuevo registro de miembro deducido.  
  
 **Usar una columna de tipo booleano para indicar si el registro actual es un miembro deducido**  
 Especifique si desea utilizar una columna booleana existente para indicar si el registro actual es un miembro deducido.  
  
 **Indicador de miembro deducido**  
 Si ha elegido utilizar una columna booleana para indicar los miembros deducidos, como se ha descrito en la opción anterior, seleccione la columna en la lista.  
  
## <a name="see-also"></a>Vea también  
 [Configurar salidas mediante el Asistente para dimensión de variación lenta](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
