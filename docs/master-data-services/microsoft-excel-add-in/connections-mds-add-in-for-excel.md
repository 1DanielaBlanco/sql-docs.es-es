---
title: Conexiones (complemento MDS para Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: ''
ms.component: microsoft-excel-add-in
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2f2b2f9d-7744-460e-83cd-56d34ea70ff0
caps.latest.revision: 12
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 86569a92d0894958c11a6416ac05d29c95c7ab3c
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="connections-mds-add-in-for-excel"></a>Conexiones (complemento MDS para Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Para descargar datos en [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], primero debe crear una conexión. Una conexión es la forma en que el servicio web [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] sabe a qué base de datos de MDS se debe conectar.  
  
 La cadena de conexión suele ser la dirección URL de la aplicación web de [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]; por ejemplo, `http://contoso/mds`.  
  
 Cada vez que inicia Excel, debe conectarse a un repositorio MDS. La única excepción es cuando la hoja de cálculo activa ya contiene datos administrados por MDS. En este caso, la conexión se realiza automáticamente cada vez que se actualizan o publican datos en la hoja.  
  
 Puede crear varias conexiones. La conexión a la que se ha obtenido acceso más recientemente se considera la predeterminada.  
  
 Pueden conectarse varios usuarios a la vez. Sin embargo, pueden surgir conflictos cuando varios usuarios intentan publicar los mismos datos. Para obtener más información, consulte [Información general: Importación de datos desde Excel &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md).  
  
## <a name="connect-automatically-and-load-frequently-used-data"></a>Conectar automáticamente y cargar datos utilizados con frecuencia  
 Si desea conectarse al mismo servidor y cargar siempre el mismo conjunto de datos, puede crear archivos de consulta de acceso directo, que contienen la información de conexión y filtro. Para obtener más información sobre los archivos de consulta, consulte [Archivos de consulta de acceso directo &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/shortcut-query-files-mds-add-in-for-excel.md).  
  
## <a name="data-quality-services"></a>Data Quality Services  
 [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] incluye la funcionalidad Data Quality Services para ayudarle a comparar los datos antes de publicarlos en el repositorio MDS. Cuando se realiza una conexión, si hay una base de datos de DQS instalada en la misma instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que la base de datos de MDS, podrá ver los botones de DQS en la cinta de opciones. Si la base de datos DQS_Main no existe en la instancia, estos botones no se muestran y la funcionalidad de calidad de los datos no está disponible.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Descripción de la tarea|Tema|  
|----------------------|-----------|  
|Crear una conexión a una base de datos de [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .|[Conectarse a un repositorio MDS &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md)|  
|Cargar datos MDS en Excel.|[Export Data to Excel from Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)|  
|Filtrar los datos MDS antes de cargarlos en Excel.|[Filtrar los datos antes de exportar &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/filter-data-before-exporting-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Contenido relacionado  
  
-   [Información general: Exportar datos a Excel &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
-   [Archivos de consulta de acceso directo &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/shortcut-query-files-mds-add-in-for-excel.md)  
  
-   [Complemento Master Data Services para Microsoft Excel](../../master-data-services/microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)  
  
  
