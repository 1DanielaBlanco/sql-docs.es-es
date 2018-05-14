---
title: Propiedades DAX | Documentos de Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e683c5b99bee1b19e7d57e31b65983bb27561537
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="dax-properties"></a>Propiedades de DAX
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
   La sección DAX de msmdsrv.ini contiene la configuración usada para controlar ciertos comportamientos de consulta en [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], como el límite superior en el número de filas que se devuelve en un conjunto de resultados de consulta DAX.

  Cuando los conjuntos de filas son muy grandes, como los devueltos en los modelos DirectQuery, el valor predeterminado de un millón de filas podría no ser suficiente. Sabrá si el límite tiene que ajustarse si recibe este error: "El conjunto de resultados de una consulta de origen de datos externo superó el tamaño máximo permitido de '1000000' filas".

Para aumentar el límite superior, especifique la configuración **MaxIntermediateRowSize** . Deberá agregar manualmente el elemento completo a la sección DAX del archivo de configuración. La configuración no estará presente en el archivo hasta que lo agregue.

## <a name="configuration-snippet"></a>Fragmento de código de la configuración

```
<ConfigurationSettings>
. . .
<DAX>
  <PredicateCheckSpoolCardinalityThreshold>5000
  </PredicateCheckSpoolCardinalityThreshold>
  <DQ>
     <MaxIntermediateRowsetSize>1000000
     </MaxIntermediateRowsetSize>
  </DQ>
</DAX>
. . .
```

## <a name="property-descriptions"></a>Descripciones de las propiedades

Configuración |Value |Description
--------|-------|-----------
MaxIntermediateRowsetSize | 1000000 | Número máximo de filas devueltas en una consulta DAX. Agregue esta entrada manualmente al archivo msmdsrv.ini y aumente el valor predeterminado si este es demasiado bajo.
PredicateCheckSpoolCardinalityThreshold| 5000 | Propiedad avanzada que no debería cambiar, salvo a petición de expertos en soporte técnico de Microsoft.

Para más información sobre otras propiedades de servidor y cómo establecerlas, vea [Configurar las propiedades de servidor en Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).
