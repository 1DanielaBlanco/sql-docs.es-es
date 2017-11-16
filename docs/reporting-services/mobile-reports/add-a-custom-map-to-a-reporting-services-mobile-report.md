---
title: "Agregar un mapa personalizado a un informe de Reporting Services móvil | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd259b95-bb58-4eb1-a436-6aa12fc6f5f2
caps.latest.revision: "6"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 6030bbac7cced5ed1ee60a2a34d505074a4a5f04
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="add-a-custom-map-to-a-reporting-services-mobile-report"></a>Agregar un mapa personalizado a un informe de Reporting Services móvil
Los mapas personalizados requieren dos archivos:  
* Un archivo .SHP para geometrías de formas  
* Un archivo .DBF para metadatos  
  
Obtenga más información sobre los [Mapas personalizados en informes para dispositivos móviles de Reporting Services](../../reporting-services/mobile-reports/custom-maps-in-reporting-services-mobile-reports.md).  
  
Almacene ambos archivos en la misma carpeta. Los nombres de los dos archivos deben coincidir (por ejemplo, canada.shp y canada.dbf). Los metadatos (archivo DBF) deben incluir el campo "NAME" con el valor del nombre de la forma correspondiente (clave), que se usará para rellenar el mapa con datos.   
  
## <a name="load-a-custom-map"></a>Cargar un mapa personalizado  
  
1. En la pestaña **Diseño** , seleccione un tipo de mapa: **Gradient Heat Map**(Mapa térmico de degradado), **Range Stop Heat Map**(Mapa térmico de umbrales de rangos) or **Bubble Map**(Mapa de burbujas), arrástrelo a la superficie de diseño y desígnele el tamaño que desee.  
  
   ![SSMRP_MapsGallery](../../reporting-services/mobile-reports/media/ssmrp-mapsgallery.png)  
  
2. En la vista **Diseño** > panel **Propiedades visuales** > **Mapa**, seleccione **Mapa personalizado de archivo**.   
  
   ![SSMRP_SelectCustomMap](../../reporting-services/mobile-reports/media/ssmrp-selectcustommap.png)  
  
3. En el cuadro de diálogo **Abrir** , vaya a la ubicación de los archivos SHP y DBF y seleccione ambos.   
  
   ![SSMRP_SelectDBFandSHP](../../reporting-services/mobile-reports/media/ssmrp-selectdbfandshp.png)  
  
## <a name="connect-data-to-a-custom-map"></a>Conectar datos a un mapa personalizado  
Cuando agregue un mapa personalizado a su informe por primera vez, [!INCLUDE[SS_MobileReptPub_Short](../../includes/ss-mobilereptpub-short.md)] lo rellena con datos geográficos simulados.  
  
![SSMRP_MapsData](../../reporting-services/mobile-reports/media/ssmrp-mapsdata.png)  
  
Mostrar datos reales en el mapa personalizado es igual que mostrarlos en los mapas integrados. Siga los pasos que aparecen en [Mapas de informes de Reporting Services móviles](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md) para mostrar los datos.  
  
### <a name="see-also"></a>Vea también  
- [Custom maps in Reporting Services mobile reports](../../reporting-services/mobile-reports/custom-maps-in-reporting-services-mobile-reports.md)  
- [Mapas de informes de Reporting Services móviles](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)  
- [Create and publish mobile reports with SQL Server Mobile Report Publisher (Creación y publicación de informes móviles con el Publicador de informes de SQL Server Mobile)](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)   
  
  
  
  
