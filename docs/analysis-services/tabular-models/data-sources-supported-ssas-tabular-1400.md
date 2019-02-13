---
title: Orígenes de datos admitidos en modelos tabulares 1400 de Analysis Services de SQL Server | Microsoft Docs
ms.date: 02/12/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4c900c6f1683b9f4c96355a759c604022515d2ce
ms.sourcegitcommit: 89a7bd9ccbcb19bb92a1f4ba75576243a58584e8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2019
ms.locfileid: "56159760"
---
# <a name="data-sources-supported-in-sql-server-analysis-services-tabular-1400-models"></a>Orígenes de datos admiten en SQL Server Analysis Services, los modelos tabulares 1400

[!INCLUDE[ssas-appliesto-sql2017](../../includes/ssas-appliesto-sql2017.md)]

En este artículo se describe los tipos de orígenes de datos que se pueden usar con modelos tabulares de SQL Server Analysis Services (SSAS) en el nivel de compatibilidad 1400. 

Para los modelos tabulares de SSAS en los niveles de compatibilidad 1200 y versiones inferiores, consulte [orígenes de datos admitidos en modelos tabulares 1200 de SQL Server Analysis Services](data-sources-supported-ssas-tabular.md).

Para Azure Analysis Services, consulte [orígenes de datos admitidos en Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource).


## <a name="cloud-data-sources"></a>Orígenes de datos en la nube

|Origen de datos  |En la memoria  |DirectQuery  |
|---------|---------|---------|
|Se aplica a: Base de datos SQL de Azure     |   Sí      |    Sí      |
|Almacenamiento de datos SQL de Azure     |   Sí      |   Sí       |
|Azure Blob Storage     |   Sí       |    No      |
|Azure Table Storage    |   Sí       |    No      |
|Azure Cosmos DB     |  Sí        |  No        |
|Azure Data Lake Store (Gen1)<sup>[1](#gen2)</sup>      |   Sí       |    No      |
|HDFS de HDInsight de Azure    |     Sí     |   No       |
|Azure HDInsight Spark <sup> [2](#databricks)</sup>     |   Sí       |   No       |
||||

<a name="gen2">1</a> -Gen2 ADLS no se admite actualmente.   
<a name="databricks">2</a> : azure Databricks mediante el conector no se admite actualmente de Spark.   



**Proveedor**   
En la memoria y los modelos DirectQuery conectarse a orígenes de datos de Azure usan .NET Framework Data Provider para SQL Server.

## <a name="on-premises-data-sources"></a>Orígenes de datos locales

### <a name="supported-by-in-memory-and-directquery-models"></a>Compatible con in-memory y los modelos DirectQuery

|Origen de datos | Proveedor en memoria | Proveedor de DirectQuery |
|  --- | --- | --- |
| SQL Server |SQL Server Native Client 11.0, proveedor Microsoft OLE DB para SQL Server, proveedor de datos de .NET Framework para SQL Server | Proveedor de datos de .NET Framework para SQL Server |
| Almacenamiento de datos SQL Server |SQL Server Native Client 11.0, proveedor Microsoft OLE DB para SQL Server, proveedor de datos de .NET Framework para SQL Server | Proveedor de datos de .NET Framework para SQL Server |
| Oracle |Proveedor Microsoft OLE DB para Oracle, proveedor de datos de Oracle para .NET |Proveedor de datos de Oracle para .NET | |
| Teradata |Proveedor OLE DB para Teradata, proveedor de datos de Teradata para .NET |Proveedor de datos de Teradata para .NET | |
| | | |

> [!NOTE]
> Para los modelos en memoria, los proveedores OLE DB pueden proporcionar un mejor rendimiento para los datos a gran escala. Al elegir entre diferentes proveedores para el mismo origen de datos, pruebe primero el proveedor OLE DB.  

### <a name="supported-by-in-memory-models-only"></a>Admite solo los modelos en memoria

|Base de datos  |
|---------|---------|---------|
|Base de datos de Access     | 
|SQL Server Analysis Services     | 
|IBM Informix (beta) | 
|Documento JSON     | 
|Líneas del archivo binario     | 
|Base de datos de MySQL     | 
|Base de datos de PostgreSQL    | Sí | No
|SAP HANA   | Sí | No
|SAP Business Warehouse    | Sí | No
|Base de datos de Sybase     | Sí | No
|||

|Archivo  |  
|---------|---------|
|Libro de Excel     |
|Carpeta     | 
|JSON | 
|Texto o CSV    | 
|Tabla XML    | 
|||

|Servicios en línea  |  
|---------|---------|
|Dynamics 365      |
|Exchange Online     |
|Objetos de Salesforce    | 
|Informes de Salesforce     |
|Lista de SharePoint Online     |
|||

|Otros  |  
|---------|---------|
|Active Directory      | 
|Exchange     |  
|Fuente de OData     | 
|Consulta ODBC     | 
|OLE DB  | 
|Lista de SharePoint | 
|||

## <a name="see-also"></a>Vea también

[Orígenes de datos compatibles en SQL Server Analysis Services, los modelos tabulares 1200](data-sources-supported-ssas-tabular.md)

[Orígenes de datos admitidos en Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource)   
