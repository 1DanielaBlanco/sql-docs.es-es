---
title: Crear un Alias para una columna de modelo | Documentos de Microsoft
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c7f7a6139adb75c9a041238e4c8f911bb88ff711
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
ms.locfileid: "34019102"
---
# <a name="create-an-alias-for-a-model-column"></a>Crear un alias para una columna de modelo
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  En [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], puede crear un alias para una columna de modelo. Esto puede resultar útil cuando el nombre de la estructura de minería de datos es demasiado largo para trabajar con él fácilmente, o si desea cambiar el nombre de la columna para que describa mejor su contenido o su uso en el modelo. Por ejemplo, si realiza una copia de una columna de estructura y, a continuación, discretiza la columna de manera diferente para un modelo determinado, puede cambiar el nombre de la columna para reflejar con más precisión el contenido.  
  
 Para crear un alias para una columna de modelo, utilice el panel **Propiedades** y establezca la propiedad [Name](../../analysis-services/scripting/properties/name-element-assl.md) de la columna.  
  
 En la pestaña **Modelos de minería de datos** del Diseñador de minería de datos, el alias parece entre paréntesis al lado de la etiqueta de uso de columna.  
  
 Para más información sobre cómo establecer las propiedades de un modelo de minería de datos, vea [Columnas del modelo de minería de datos](../../analysis-services/data-mining/mining-model-columns.md).  
  
### <a name="to-add-an-alias-to-a-mining-model-column"></a>Para agregar un alias a una columna de modelo de minería de datos  
  
1.  En la pestaña **Modelos de minería de datos** del Diseñador de minería de datos, haga clic con el botón derecho en la celda del modelo de minería perteneciente a la columna que quiere cambiar y, luego, seleccione **Propiedades**.  
  
2.  En la ventana **Propiedades** situada a la derecha de la pantalla, haga clic en la celda existente junto a la propiedad Name y elimine el valor actual. Escriba un nuevo nombre para la columna.  
  
## <a name="see-also"></a>Vea también  
 [Tareas y tareas de modelo de minería de datos](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Propiedades del modelo de minería de datos](../../analysis-services/data-mining/mining-model-properties.md)  
  
  
