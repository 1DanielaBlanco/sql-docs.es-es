---
title: Valores atípicos (datos de SQL Server a los complementos de minería de datos) | Documentos de Microsoft
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- exceptions [data mining]
- data preparation
- outliers [data mining]
- data cleaning
ms.assetid: e6fa7c62-4005-4792-9211-3b699377a517
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 48073f6ce9c1d5836d85cf468b2b9a45256f8163
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36106426"
---
# <a name="outliers-sql-server-data-mining-add-ins"></a>Valores atípicos (Complementos de minería de datos de SQL Server)
  ![Asistente valores atípicos en la cinta de opciones de minería de datos](media/dmc-outliers.gif "Asistente valores atípicos en la cinta de opciones de minería de datos")  
  
 Un *valores atípicos* significa un valor de datos que es problemático por alguno de los siguientes motivos:  
  
-   El valor está fuera del intervalo esperado.  
  
-   Es posible que los datos se hayan especificado de forma incorrecta.  
  
-   El valor es un valor ausente.  
  
-   Los datos consisten en un espacio u otra cadena de tipo NULL.  
  
-   El valor es preciso pero está tan alejado de la distribución que puede afectar significativamente al modelo.  
  
 El Cliente de minería de datos para Excel le ayuda a detectar estos datos y a actualizar los valores o a suprimirlos. Por ejemplo, puede reemplazar los valores atípicos por una media aritmética o puede eliminar las filas que sean susceptibles de contener valores erróneos.  
  
## <a name="handling-outliers"></a>Tratar los valores atípicos  
 El **quitar valores atípicos** asistente ofrece varias herramientas para controlar valores atípicos adecuadamente:  
  
-   Primero, puede explorar los datos para entender mejor la distribución de los valores y la relación de los valores atípicos con los otros datos.  
  
     Por ejemplo, puede usar el **explorar datos** tarea para revisar y corregir los valores. El **quitar valores atípicos** asistente también muestra un gráfico, una línea o un gráfico de barras, para ayudarle a comprender la distribución de todos los valores.  
  
-   A continuación, puede usar el **valores atípicos** Asistente para quitar o cambiar los valores atípicos. El método que use dependerá de si los valores son discretos o continuos.  
  
     El asistente muestra los valores discretos en un gráfico de barras, donde cada barra representa un valor concreto y el alto de la barra indica el número de casos para cada valor. Deslizando el control de umbral en el gráfico, puede cortar barras que representen grupos de valores extremos o potencialmente erróneos.  
  
-   El asistente muestra los valores continuos en un gráfico de barras o en un gráfico de líneas. En el gráfico de líneas, el valor está representado en el eje X y el recuento de los valores en el eje Y.  
  
     Puede controlar si se debe quitar o mantener los valores en los extremos inferior y superior del gráfico cambiando la **mínimo** y **máximo** valores o Deslizar las barras. Cuando se cambia la configuración de valor mínimo y máximo, los datos que se van a eliminar se muestran con un sombreado en el gráfico.  
  
 Una vez seleccionados los valores atípicos con los que va a trabajar, debe indicar al asistente cómo tiene que tratar dichos valores. Puede eliminar las filas que contienen los valores atípicos o puede especificar un valor de reemplazo, como un valor promedio, un valor NULL u otro valor de su elección.  
  
 Finalmente, el asistente le da algunas opciones para mostrar los nuevos datos. Puede reemplazar los datos originales por valores nuevos, agregar a la tabla una nueva columna que contenga los nuevos valores, o crear una nueva hoja de cálculo que contenga los datos actualizados.  
  
### <a name="using-the-outlier-wizard"></a>Usar el Asistente para quitar valores atípicos  
  
1.  En el **minería de datos** la cinta de opciones, haga clic en **limpiar datos**y seleccione **valores atípicos**.  
  
2.  En el **seleccionar datos de origen** cuadro de diálogo, seleccione una tabla de datos de Excel o un rango de celdas y haga clic en **siguiente**.  
  
    > [!WARNING]  
    >  No se puede utilizar el **valores atípicos** asistente en datos externos, a menos que se copie a Excel primero.  
  
3.  En el **Seleccionar columna** cuadro de diálogo, seleccione un **único** columna.  
  
     Haga clic en **Siguiente**.  
  
4.  En el **especificar umbrales** diálogo cuadro, revise la distribución de datos.  
  
    -   Si la columna contiene valores discretos, el asistente muestra un histograma que contiene el recuento para cada valor discreto.  
  
         Suponiendo que los valores atípicos son valores extraños, puede filtrarlos cambiando el **mínimo** valor.  
  
    -   Si la columna contiene datos numéricos, puede hacer clic en el **ver como discreto** botón o **ver como numérico** botón para alternar entre ver los valores en un gráfico de barras o un gráfico de líneas.  
  
5.  En el **especificar umbrales** diálogo cuadro, seleccione el rango de datos que desea conservar escribiendo un valor mínimo y máximo o arrastrando las barras deslizantes. Haga clic en **Siguiente**.  
  
6.  En el **tratamiento de valores atípicos** diálogo cuadro, especifique si desea que los valores para eliminarse o reemplazarse y haga clic en **siguiente**.  
  
7.  En el **Seleccionar destino** diálogo cuadro, especifique dónde desea los nuevos datos se guarden.  
  
### <a name="related-options"></a>Opciones relacionadas  
 El asistente proporciona estas opciones:  
  
|**Opciones**|**Comentario**|  
|-----------------|-----------------|  
|**Seleccionar columna**|Solo se puede trabajar con una columna cada vez.|  
|**Especifique el tratamiento de los umbrales**|Establezca un umbral en **mínimo** para excluir los valores que se encuentran en menos filas que el valor de umbral.<br /><br /> Inicialmente, el valor en **mínimo** es igual que el valor de las filas mínimas, y no se puede hacer que el mínimo inferior a ese valor.|  
|**Tratamiento de valores atípicos**|Si decide eliminar los valores atípicos, puede o cambiar los datos de la hoja de cálculo actual o bien crear una copia de los datos en una nueva hoja de cálculo.|  
  
## <a name="see-also"></a>Vea también  
 [Explorar datos &#40;complementos de minería de datos de SQL Server&#41;](explore-data-sql-server-data-mining-add-ins.md)  
  
  