---
title: Ver o cambiar marcas de modelado (minería de datos) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d1169735-fb18-417b-b8d6-9a161e444020
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5ca890dca3e0ffb966f1b87a745b189db4af6d81
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="view-or-change-modeling-flags-data-mining"></a>Ver o cambiar marcas de modelado (minería de datos)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Las marcas de modelado son propiedades que se activan en una columna de estructura de minería de datos o columnas de modelo de minería de datos para controlar cómo procesa los datos el algoritmo durante el análisis.  
  
 En el Diseñador de minería de datos, puede ver y modificar las marcas de modelado asociadas a una estructura de minería de datos o a una columna de minería de datos examinando las propiedades de la estructura o del modelo. También puede establecer las marcas de modelado utilizando DMX, AMO o XMLA.  
  
 Este procedimiento describe cómo cambiar las marcas de modelado en el diseñador.  
  
### <a name="view-or-change-the-modeling-flag-for-a-structure-column-or-model-column"></a>Ver o cambiar la marca de modelado de una columna de la estructura o columna del modelo  
  
1.  En SQL Server Design Studio, abra el Explorador de soluciones y, a continuación, haga doble clic en la estructura de minería de datos.  
  
2.  Para establecer la marca de modelado NOT NULL, haga clic en la pestaña **Estructura de minería de datos** . Para establecer las marcas REGRESSOR o MODEL_EXISTENCE_ONLY, haga clic en la pestaña **Modelo de minería de datos** .  
  
3.  Haga clic con el botón derecho en la columna que quiere ver o cambiar y seleccione **Propiedades**.  
  
4.  Para agregar una nueva marca de modelado, haga clic en el cuadro de texto situado junto a la propiedad **ModelingFlags** y active la casilla o casillas de las marcas de modelado que desea utilizar.  
  
     Las marcas de modelado solo se muestran si son adecuadas para el tipo de datos de la columna.  
  
    > [!NOTE]  
    >  Después de cambiar una marca de modelado, debe volver a procesar el modelo.  
  
### <a name="get-the-modeling-flags-used-in-the-model"></a>Obtener las marcas de modelado utilizadas en el modelo  
  
-   En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], abra una ventana Consulta DMX y escriba una consulta como la siguiente:  
  
    ```  
    SELECT COLUMN_NAME, CONTENT_TYPE, MODELING_FLAG  
    FROM $system.DMSCHEMA_MINING_COLUMNS  
    WHERE MODEL_NAME = 'Forecasting'  
  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Tareas y tareas de modelo de minería de datos](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Modelado marcas & #40; minería de datos & #41;](../../analysis-services/data-mining/modeling-flags-data-mining.md)  
  
  
