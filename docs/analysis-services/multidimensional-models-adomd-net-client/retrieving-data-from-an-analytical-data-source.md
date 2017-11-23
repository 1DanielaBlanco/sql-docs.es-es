---
title: "Recuperar datos de un origen de datos analíticos | Documentos de Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- data retrieval [ADOMD.NET]
- retrieving data
- ADOMD.NET, data retrieval
- data retrieval [ADOMD.NET], about retrieving data
ms.assetid: 88358189-28aa-4bc7-8dda-5a92e3a012b8
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e2dbd10be43b0d0e64b4068e6f93c0bba2457d4e
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="retrieving-data-from-an-analytical-data-source"></a>Recuperar datos de un origen de datos analíticos
  Una vez que realiza una conexión y crea la consulta, puede recuperar cualquier dato. En ADOMD.NET, también puede recuperar los datos mediante tres objetos distintos (<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>, <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>, y <xref:System.Xml.XmlReader>) llamando a uno de los **Execute** métodos de la <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> objeto.  
  
 Cada uno de estos tres objetos equilibra la interactividad y la sobrecarga:  
  
-   *Interactividad* hace referencia a la facilidad de uso y la cantidad de información disponible a través del modelo de objeto.  
  
-   *Sobrecarga* hace referencia a la cantidad de tráfico que genera un modelo de objetos a través de la conexión de red al servidor, la cantidad de memoria necesaria para el modelo de objetos y la velocidad con la que el modelo de objetos recupera datos.  
  
 Para ayudarle a seleccionar el objeto de recuperación de datos que mejor se ajusta a las necesidades de su aplicación, en la tabla siguiente se resaltan las diferencias entre interactividad y sobrecarga para cada objeto.  
  
|Object|Interactividad|Sobrecarga|Conserva las dimensiones|Información de uso|  
|------------|-------------------|--------------|----------------------------|-----------------------|  
|<xref:Microsoft.AnalysisServices.AdomdClient.CellSet>|Máxima|Ligeramente elevada, lo que da como resultado una recuperación más lenta de los datos|Sí|[Recuperación de datos mediante el objeto CellSet](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-cellset.md)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataAdapter>|Moderada|Moderada|No|[Llenar un DataSet desde un DataAdapter](http://go.microsoft.com/fwlink/?LinkId=70016)|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|Moderada|Moderada|No|[Recuperación de datos mediante AdomdDataReader](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-adomddatareader.md)|  
|<xref:System.Xml.XmlReader>|Más bajo|Mínima, lo que da como resultado una recuperación más rápida de los datos|Sí|[Recuperación de datos mediante XmlReader](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-data-using-the-xmlreader.md)|  
  
## <a name="see-also"></a>Vea también  
 [Programación del cliente de ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)  
  
  
