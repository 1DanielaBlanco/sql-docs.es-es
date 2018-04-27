---
title: Opciones de atributos fijos y variables (Asistente para dimensiones de variación lenta) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: data-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.dts.loaddimwizard.attriboption.f1
ms.assetid: c841345c-7d03-452f-9379-1c8c464f029c
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7f8481b4e3b4044a53c09273caf20d7123b3f366
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="fixed-and-changing-attribute-options-slowly-changing-dimension-wizard"></a>Opciones de atributos fijos y variables (Asistente para dimensiones variables)
  Utilice el cuadro de diálogo **Opciones de atributos fijos y variables** para especificar cómo se debe responder a los cambios realizados en los atributos fijos y variables.  
  
 Para obtener más información acerca de este asistente, vea [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Opciones  
 **Atributos fijos**  
 En el caso de los atributos fijos, indique si la tarea debe dar un error cuando se detecte un cambio en un atributo fijo.  
  
 **Atributos variables**  
 En el caso de los atributos variables, indique si la tarea debe cambiar todos los registros no actualizados o expirados, además de los actuales, cuando se detecten cambios en un atributo variable. Los registros expirados son los que se han reemplazado por uno nuevo mediante un cambio en un atributo histórico (un cambio del Tipo 2). La selección de esta opción puede imponer requisitos adicionales de procesamiento en un objeto multidimensional generado en el almacenamiento de datos relacional.  
  
## <a name="see-also"></a>Ver también  
 [Configurar salidas mediante el Asistente para dimensión de variación lenta](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
