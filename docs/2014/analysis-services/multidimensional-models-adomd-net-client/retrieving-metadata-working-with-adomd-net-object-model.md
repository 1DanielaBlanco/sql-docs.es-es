---
title: Trabajar con el modelo de objetos de ADOMD.NET | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- metadata [ADOMD.NET]
- object model (client) [ADOMD.NET]
- retrieving metadata
ms.assetid: 0183dcdc-f2ea-4246-ad00-6e8ccc9d8217
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: de2d73db65d10acdea5ec0c221eb994700ba5f41
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36196556"
---
# <a name="working-with-the-adomdnet-object-model"></a>Trabajar con el modelo de objetos ADOMD.NET
  ADOMD.NET proporciona un modelo de objetos que permite ver los cubos y los objetos subordinados que contiene un origen de datos analíticos. Sin embargo, no todos los metadatos para un origen de datos analíticos determinado están disponibles a través del modelo de objetos. El modelo de objetos proporciona acceso únicamente a la información más útil para que se muestre una aplicación cliente y permitir que un usuario construya comandos interactivamente. Debido a la complejidad reducida de los metadatos para presentar, el modelo de objetos ADOMD.NET es más fácil de usar.  
  
 En el modelo de objetos ADOMD.NET, el objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> proporciona acceso a la información de cubos de procesamiento analítico en línea (OLAP) y modelos de minería definidos en un origen de datos analíticos, así como de objetos relacionados como dimensiones, conjuntos con nombre, y algoritmos de minería de datos.  
  
## <a name="retrieving-olap-metadata"></a>Recuperar metadatos de OLAP  
 Cada objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> tiene una colección de objetos <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> que representa los cubos disponible para el usuario o aplicación. El objeto <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> expone información acerca del cubo, así como varios objetos relacionados con el cubo, como dimensiones, indicadores de rendimiento clave, medidas, conjuntos con nombre, etc.  
  
 Siempre que sea posible, debería usar el objeto <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> para representar metadatos en aplicaciones cliente diseñadas para admitir varios servidores OLAP o para mostrar y obtener acceso a metadatos generales.  
  
> [!NOTE]  
>  Para metadatos específicos del proveedor, o para mostrar y obtener acceso detallado a metadatos, use conjuntos de filas de esquema para recuperar metadatos. Para obtener más información, consulte [trabajar con conjuntos de filas de esquema en ADOMD.NET](retrieving-metadata-working-with-schema-rowsets.md)).  
  
 En el ejemplo siguiente se usa el objeto <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> para recuperar los cubos visibles y sus dimensiones del servidor local:  
  
 [!code-csharp[Adomd.NetClient#RetrieveCubesAndDimensions](../../snippets/csharp/SQL14/adomd.net/adomd.netclient/cs/adomdexample.cs#retrievecubesanddimensions)]  
  
## <a name="retrieving-data-mining-metadata"></a>Recuperar metadatos de minería de datos  
 Cada objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> tiene varias colecciones que proporcionan información sobre las capacidades de la minería de datos del origen de datos:  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelCollection> contiene una lista de cada modelo de minería de datos del origen de datos.  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningServiceCollection> proporciona información sobre los algoritmos de minería de datos disponibles.  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningStructureCollection> expone información sobre las estructuras de minería de datos del servidor.  
  
 Para determinar cómo consultar contra un modelo de minería en el servidor, realice iteraciones en la colección <xref:Microsoft.AnalysisServices.AdomdServer.MiningModel.Columns%2A>. Cada objeto <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn> expone las características siguientes:  
  
-   Si el objeto es una columna de entrada (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.IsInput%2A>).  
  
-   Si el objeto es una columna de predicción (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.IsPredictable%2A>).  
  
-   Los valores asociados a una columna discreta (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.Values%2A>)  
  
-   El tipo de datos de la columna (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.Type%2A>).  
  
## <a name="see-also"></a>Vea también  
 [Recuperación de metadatos de un origen de datos analíticos](retrieving-metadata-from-an-analytical-data-source.md)  
  
  