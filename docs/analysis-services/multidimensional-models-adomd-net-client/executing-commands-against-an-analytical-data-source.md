---
title: Ejecutar comandos en un origen de datos analíticos | Documentos de Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 01f7c32643c4e0a48f2451de37729f919b057208
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="executing-commands-against-an-analytical-data-source"></a>Ejecutar comandos en un origen de datos analíticos
  Después de establecer una conexión a un origen de datos analíticos, puede usar un objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> para ejecutar con comandos y resultados devueltos de ese origen de datos. Estos comandos pueden recuperar datos mediante expresiones multidimensionales (MDX), extensiones de minería de datos (DMX), o incluso una sintaxis limitada de SQL. Además, puede usar los comandos ASSL (Analysis Services Scripting Language) para modificar la base de datos subyacente.  
  
## <a name="creating-a-command"></a>Crear un comando  
 Antes de ejecutar un comando, debe crearlo. Puede crear un comando mediante uno de los dos métodos siguientes:  
  
-   El primer método usa el constructor <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>, que puede tomar un comando para ejecutarlo en el origen de datos y un objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> para ejecutar el comando.  
  
-   El segundo método usa el método <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.CreateCommand%2A> del objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
 El texto del comando para ejecutar se puede consultar y modificar mediante la propiedad <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.CommandText%2A>. Los comandos que crea no tienen que devolver los datos después de ejecutarse.  
  
## <a name="running-a-command"></a>Ejecutar un comando  
 Después de crear un objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand>, hay varios métodos <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.Execute%2A> que el comando puede usar para realizar varias acciones. En la tabla siguiente se enumeran algunas de estas acciones.  
  
|A|Use este método|  
|--------|---------------------|  
|Devolver resultados como un flujo de datos|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteReader%2A> para devolver un objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdDataReader>|  
|Devolver un objeto <xref:Microsoft.AnalysisServices.AdomdClient.CellSet>|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteCellSet%2A>|  
|Ejecutar comandos que no devuelven filas|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteNonQuery%2A>|  
|Devolver un **XMLReader** objeto que contiene los datos de XML for formato compatible con Analysis (XMLA)|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand.ExecuteXmlReader%2A>|  
  
### <a name="example-of-running-a-command"></a>Ejemplo de cómo ejecutar un comando  
 Este ejemplo se utiliza la <xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> para ejecutar un comando XMLA que procesará el **Adventure Works DW** cubo en el servidor local, sin devolver los datos.  
  
 [!code-cs[Adomd.NetClient#ExecuteXMLAProcessCommand](../../analysis-services/multidimensional-models-adomd-net-client/codesnippet/csharp/executing-commands-again_1.cs)]  
  
  
