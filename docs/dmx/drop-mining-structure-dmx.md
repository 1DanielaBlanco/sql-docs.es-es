---
title: "QUITAR LA ESTRUCTURA DE MINERÍA DE DATOS (DMX) | Documentos de Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP MINING STRUCTURE
- DROP_MINING_STRUCTURE
dev_langs: DMX
helpviewer_keywords:
- removing mining structures
- dropping mining structures
- DROP MINING STRUCTURE statement
- deleting mining structures
- mining structures [DMX], deleting
ms.assetid: 30df8c36-3a15-4d8c-98f3-0f8917be9fc8
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 955b0c8a70cf7b051515f88ff1c73a593522e873
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="drop-mining-structure-dmx"></a>DROP MINING STRUCTURE (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Quita la estructura de minería de datos especificada de la base de datos. También se quitan de la base de datos todos los modelos de minería de datos asociados con la estructura.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
DROP MINING STRUCTURE <structure>  
```  
  
## <a name="arguments"></a>Argumentos  
 *estructura*  
 Identificador de estructura.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se quita de la base de datos la estructura de minería de datos New Mailing.  
  
```  
DROP MINING STRUCTURE [New Mailing]  
```  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de minería de datos &#40; DMX &#41; Instrucciones de definición de datos](../dmx/dmx-statements-data-definition.md)   
 [Extensiones de minería de datos &#40; DMX &#41; Instrucciones de manipulación de datos](../dmx/dmx-statements-data-manipulation.md)   
 [Referencia de instrucciones de Extensiones de minería de datos &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
