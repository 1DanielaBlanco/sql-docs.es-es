---
title: Conjuntos de filas de esquema de Analysis Services | Documentos de Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- SSAS, data access interfaces
- Analysis Services data access interfaces, schema rowsets
- data access interfaces [Analysis Services]
- XML for Analysis, schema rowsets
- rowsets [Analysis Services], retrieving schema rowsets
- retrieving schema rowsets
- XMLA, schema rowsets
- rowsets [Analysis Services]
- schema rowsets [Analysis Services], retrieving
ms.assetid: 820d4b59-d428-4616-b792-c848e5da407e
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6be6dd4c95d2c44400a202e12179cd1eb5757b2f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="analysis-services-schema-rowsets"></a>Conjuntos de filas de esquema de Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Los conjuntos de filas de esquema son tablas predefinidas que contienen información sobre los objetos de Analysis Services y el estado del servidor, como el esquema de la base de datos, sesiones activas, conexiones, comandos y trabajos que se ejecutan en el servidor. Puede consultar las tablas del conjunto de filas de esquema en una ventana de script XML/A en SQL Server Management Studio, ejecutar una consulta DMV en un conjunto de filas de esquema o crear una aplicación personalizada que incorpore la información del conjunto de filas de esquema (por ejemplo, una aplicación de informes que recupere la lista de dimensiones disponibles que se pueden utilizar para crear un informe).  
  
> [!NOTE]  
>  Si usa conjuntos de filas de esquema de XML/A un script, la información que se devuelve en el *resultado* parámetro de la [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) método se estructura según los diseños de columna de conjunto de filas que se describe en esta sección. El proveedor de [!INCLUDE[msCoName](../../includes/msconame-md.md)] XML for Analysis (XMLA) admite los conjuntos de filas requeridos por XML para la especificación del análisis. El proveedor XMLA también admite algunos de los conjuntos de filas de esquema estándar para OLE DB, OLE DB para OLAP y OLE DB para los proveedores de origen de datos de minería de datos. Los conjuntos de filas admitidos se describen en los siguientes temas.  
  
## <a name="in-this-section"></a>En esta sección  
  
|Tema|Description|  
|-----------|-----------------|  
|[XML para conjuntos de filas de esquema de análisis](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)|Describe los conjuntos de filas XMLA admitidos por el proveedor XMLA.|  
|[Conjuntos de filas de esquema OLE DB](../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)|Describe los conjuntos de filas de esquema de OLE DB admitidos por el proveedor XMLA.|  
|[OLE DB para OLAP Schema Rowsets](../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)|Describe la OLE DB para los conjuntos de filas de esquema OLAP admitidos por el proveedor XMLA.|  
|[Conjuntos de filas de esquema de minería de datos](../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)|Describe los conjuntos de filas de esquema de minería de datos admitidos por el proveedor XMLA.|  
  
## <a name="see-also"></a>Vea también  
 [Acceso a datos de modelo multidimensional & #40; Analysis Services - datos multidimensionales & #41;](../../analysis-services/multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)   
 [Usar dinámica vistas de administración & #40; DMV & #41; para supervisar Analysis Services](../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
