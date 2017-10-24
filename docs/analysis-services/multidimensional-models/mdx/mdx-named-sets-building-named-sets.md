---
title: Crear conjuntos con nombre en MDX (MDX) | Documentos de Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], named sets
- named sets [MDX]
- sets [MDX]
- MDX [Analysis Services], named sets
- queries [MDX], named sets
- set expressions [MDX]
ms.assetid: 213b0035-e96d-4ba0-83f2-ded206905603
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b9239f7ee621cec3032c42d10b70c75702b58db6
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-named-sets---building-named-sets"></a>MDX denominado conjuntos: crear conjuntos con nombre
  Una expresión de conjunto puede ser una declaración extensa, compleja y, por tanto, difícil de seguir o entender. O bien, una expresión de conjunto puede utilizarse con tanta frecuencia que definir repetidamente el conjunto sea fatigoso. Para facilitar el trabajo con una expresión larga, compleja o de uso habitual, las expresiones multidimensionales (MDX) permiten expresiones como un *conjunto con nombre*.  
  
 Esencialmente, un conjunto con nombre es una expresión de conjunto a la que se ha asignado un alias. Un conjunto con nombre puede incorporar miembros o funciones que se pueden incorporar normalmente a un conjunto. Como MDX trata el alias del conjunto con nombre como una expresión de conjunto, puede utilizar ese alias en cualquier lugar en que se acepte una expresión de conjunto.  
  
 Puede definir un conjunto con nombre para que tenga uno de los contextos siguientes:  
  
-   **Ámbito de consulta** Para crear un conjunto con nombre definido como parte de una consulta MDX (y, por lo tanto, con un ámbito limitado a la consulta) es necesario usar la palabra clave WITH. Puede utilizar el conjunto con nombre en una instrucción MDX SELECT. De esta manera, el conjunto con nombre creado con la palabra clave WITH se puede cambiar sin tener que tocar la instrucción SELECT.  
  
     Para más información sobre cómo usar la palabra clave WITH para crear conjuntos con nombre, vea [Crear conjuntos con nombre de ámbito de consulta &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-query-scoped-named-sets.md).  
  
-   **Ámbito de sesión** Para crear un conjunto con nombre cuyo ámbito sea más amplio que el contexto de la consulta (es decir, un ámbito que represente el período de duración de la sesión MDX) es necesario usar la instrucción CREATE SET. Un conjunto con nombre definido por la utilización de la instrucción CREATE SET está disponible para todas las consultas de MDX de esa sesión. La instrucción CREATE SET tiene sentido, por ejemplo, en una aplicación cliente que reutilice un conjunto de un modo coherente en varias consultas diferentes.  
  
     Para más información sobre cómo usar la instrucción CREATE SET para crear conjuntos de nombre en una sesión, vea [Crear conjuntos con nombre del ámbito de consulta &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-session-scoped-named-sets.md).  
  
## <a name="see-also"></a>Vea también  
 [SELECT &#40;Instrucción, MDX&#41;](../../../mdx/mdx-data-manipulation-select.md)   
 [CREAR la instrucción SET &#40; MDX &#41;](../../../mdx/mdx-data-definition-create-set.md)   
 [Aspectos básicos de las consultas MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  

