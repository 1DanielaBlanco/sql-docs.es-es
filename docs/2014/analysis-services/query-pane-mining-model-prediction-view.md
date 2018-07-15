---
title: Consultar el panel (vista predicción de modelo de minería de datos) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.prediction.query.f1
ms.assetid: fdeec72e-d0bd-4453-9eaa-46436e4d6edc
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ede17228e9dc21a170815ecc46900fd38ab7d978
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211785"
---
# <a name="query-pane-mining-model-prediction-view"></a>Panel de consulta (Vista Predicción de modelo de minería de datos)
  En el panel **Consulta** se muestran las instrucciones DMX (Extensiones de minería de datos) creadas por el Generador de consultas de predicción. Puede modificar las instrucciones y, a continuación, hacer clic en el botón **Cambiar a vista de resultado de consulta** para devolver los resultados. Si cambia a la vista **Diseño** , se perderán los cambios realizados a la instrucción.  
  
 **Para más información:** [Instrucciones de manipulación de datos de Extensiones de minería de datos &#40;DMX&#41;](/sql/dmx/dmx-statements-data-manipulation), [Crear una consulta DMX en SQL Server Management Studio](data-mining/create-a-dmx-query-in-sql-server-management-studio.md)  
  
## <a name="options"></a>Opciones  
 **Cambiar a vista de resultado de consulta**  
 Haga clic para cambiar entre los paneles **Diseño**, **Consulta**y **Resultado** . Al cambiar al panel **Resultado** se ejecuta la consulta.  
  
 **Guardar el resultado de consulta**  
 Abre el cuadro de diálogo **Guardar resultado de consulta de minería de datos** .  
  
 **Consulta singleton**  
 Le permite crear una consulta singleton, en la que proporciona los datos de entrada directamente en la consulta en lugar de proporcionar una referencia a una tabla de valores de entrada. La tabla **Seleccionar tabla(s) de entrada** se reemplaza por una tabla **Entrada de consulta singleton** . Se perderá la consulta de predicción actual si cambia a una consulta singleton.  
  
 **Actualizar los resultados de la consulta**  
 Vuelve a procesar la consulta de predicción. Esto solo está habilitado en el panel **Resultado** .  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de consultas de minería de datos](data-mining/data-mining-query-tools.md)   
 [Extensiones de minería de datos &#40;DMX&#41; referencia de instrucciones](/sql/dmx/data-mining-extensions-dmx-statements)   
 [Generador de consultas de predicción &#40;minería de datos&#41;](prediction-query-builder-data-mining.md)  
  
  
