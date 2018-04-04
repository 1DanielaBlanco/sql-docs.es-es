---
title: Los modelos tabulares | Documentos de Microsoft
ms.custom: ''
ms.date: 03/30/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Active
ms.openlocfilehash: 54cd62aa50aff198d2397843c528f09a1a2fc83b
ms.sourcegitcommit: 8f1d1363e18e0c32ff250617ab6cb2da2147bf8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2018
---
# <a name="tabular-models"></a>Modelos tabulares
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Los modelos tabulares son bases de datos de Analysis Services que se ejecutan en memoria o en el modo DirectQuery, de tal forma que se accede a los datos directamente desde los orígenes de datos relacionales de back-end. Mediante el uso de algoritmos de compresión de última generación y el procesador de consultas multiproceso, el motor de análisis ofrece un acceso rápido a datos y objetos del modelo tabular mediante la notificación de las aplicaciones cliente como Power BI y Excel.  
  
 Aunque los modelos en memoria son el valor predeterminado, DirectQuery es un modo de consulta alternativo para los modelos que son demasiado grandes para caber en memoria, o cuando la volatilidad de los datos impide una estrategia de procesamiento razonable. DirectQuery logra paridad con modelos en memoria mediante la compatibilidad con una amplia gama de orígenes de datos, capacidad para manejar tablas calculadas y columnas en un modelo de DirectQuery, seguridad de nivel de fila a través de expresiones de DAX que llegue a la base de datos back-end y las consultas optimizaciones que dan como resultado un rendimiento más rápido.
  
 Los modelos tabulares se crean en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] mediante la plantilla de proyecto de modelo Tabular que proporciona una superficie de diseño para crear un modelo, tablas, relaciones y expresiones DAX. Puede importar datos de varios orígenes y luego enriquecer el modelo agregando relaciones, columnas y tablas calculadas, medidas, KPI, jerarquías y traducciones.  
  
 Los modelos se pueden implementar en los servicios de análisis de Azure o una instancia de SQL Server Analysis Services configurado para el modo de servidor Tabular. Los modelos tabulares implementados se pueden administrar en SQL Server Management Studio. Medida que crecen los modelos, puede particiones para optimizar el procesamiento y protegerlos en el nivel de fila mediante la seguridad basada en roles.  

  
  
