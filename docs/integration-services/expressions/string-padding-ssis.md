---
title: Rellenar cadenas (SSIS) | Microsoft Docs
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
helpviewer_keywords:
- padding strings [Integration Services]
- expressions [Integration Services], string padding
- string padding
ms.assetid: d3fed73d-e0d4-4c67-9355-fb7083a72dd6
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d1b8ebb2ac36f435d5b3ca0832e22ea89876a222
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="string-padding-ssis"></a>Rellenar cadenas (SSIS)
  El evaluador de expresiones no comprueba si una cadena contiene espacios en blanco iniciales y finales, ni rellena cadenas para que tengan la misma longitud antes de compararlas. Si las expresiones requieren rellenar cadenas, puede utilizar el operador + para concatenar valores de columnas y cadenas de espacios en blanco. Para más información, vea [+ &#40;Concatenar&#41; &#40;expresión de SSIS&#41;](../../integration-services/expressions/concatenate-ssis-expression.md).  
  
 Por otra parte, si desea quitar espacios, el evaluador de expresiones proporciona las funciones LTRIM, RTRIM y TRIM, que quitan los espacios en blanco iniciales o finales, o ambos. Para más información, vea [LTRIM &#40;expresión de SSIS&#41;](../../integration-services/expressions/ltrim-ssis-expression.md), [RTRIM &#40;expresión de SSIS&#41;](../../integration-services/expressions/rtrim-ssis-expression.md) y [TRIM &#40;expresión de SSIS&#41;](../../integration-services/expressions/trim-ssis-expression.md).  
  
> [!NOTE]  
>  La función LEN incluye en el recuento los espacios en blanco iniciales y finales.  
  
## <a name="related-content"></a>Contenido relacionado  
 Artículo técnico, sobre la [referencia rápida de expresiones de SSIS](http://go.microsoft.com/fwlink/?LinkId=746575), en pragmaticworks.com  
  
  
