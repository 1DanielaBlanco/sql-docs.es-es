---
title: "Conversión de orígenes de datos (Generador de informes y SSRS) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data sources [Reporting Services], embedded
- data sources [Reporting Services], shared
ms.assetid: 0e099c7e-8c03-43eb-9ea3-76e52d9ebbe3
caps.latest.revision: "16"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: d189fc88b7f6e0ed609e1c54cdc88cbf115bc6b8
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="convert-data-sources-report-builder-and-ssrs"></a>Conversión de orígenes de datos (Generador de informes y SSRS)
  Cada origen de datos del panel Datos de informe está incrustado y es específico del informe, o está compartido. En el Generador de informes, un origen de datos compartido señala un origen de datos compartido publicado en un servidor de informes o un sitio de SharePoint. En el Diseñador de informes, un origen de datos compartido señala un origen de datos compartido de la carpeta **Orígenes de datos compartidos** en el Explorador de soluciones.  
  
 Para más información sobre las diferencias entre orígenes de datos insertados y compartidos, vea [Conexiones de datos u orígenes de datos compartidos e incrustados &#40;Generador de informes y SSRS&#41;](http://msdn.microsoft.com/library/f417782c-b85a-4c4d-8a40-839176daba56).  
  
 Para más información sobre cómo crear un origen de datos compartido, vea [Crear un origen de datos incrustado o compartido &#40;SSRS&#41;](http://msdn.microsoft.com/library/b111a8d0-a60d-4c8b-b00a-51644b19c34b).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="report-designer"></a>Diseñador de informes  
  
#### <a name="to-convert-a-data-source-from-embedded-to-shared"></a>Para convertir un origen de datos incrustado en compartido  
  
-   En el panel Datos de informe, haga clic con el botón derecho en el origen de datos y, después, haga clic en **Convertir a origen de datos compartidos**.  
  
    > [!NOTE]  
    >  Si el panel Datos de informe no está visible, haga clic en **Datos de informe** en el menú **Ver**. Si el panel se abre como una ventana flotante, puede acoplarlo. Para más información, vea [Acoplar el panel Datos de informe en el Diseñador de informes &#40;SSRS&#41;](../../reporting-services/tools/dock-the-report-data-pane-in-report-designer-ssrs.md).  
  
     En el panel Datos de informe, el icono de origen de datos cambia al icono de origen de datos compartido. En el Explorador de soluciones, aparece un origen de datos compartido con el mismo nombre bajo la carpeta **Origen de datos compartido** .  
  
### <a name="to-convert-a-data-source-from-shared-to-embedded"></a>Para convertir un origen de datos compartido en incrustado  
  
-   En el panel Datos de informe, haga clic con el botón derecho en el origen de datos, abra el cuadro de diálogo **Propiedades del origen de datos** y, después, haga clic en **Conexión incrustada**. Escriba la información requerida.  
  
     En el panel Datos de informe, el icono de origen de datos cambia al icono de origen de datos compartido.  
  
## <a name="report-builder"></a>Generador de informes  
  
#### <a name="to-convert-a-data-source-from-embedded-to-shared"></a>Para convertir un origen de datos incrustado en compartido  
  
-   En el panel Datos de informe, haga clic con el botón derecho en el origen de datos para abrir el cuadro de diálogo **Propiedades del origen de datos** y, después, haga clic en **Conexión incrustada**. Escriba la información requerida.  
  
     En el panel Datos de informe, el icono de origen de datos cambia al icono de origen de datos compartido.  
  
#### <a name="to-convert-a-data-source-from-shared-to-embedded"></a>Para convertir un origen de datos compartido en incrustado  
  
-   En el panel Datos de informe, haga clic con el botón derecho en el origen de datos, abra el cuadro de diálogo **Propiedades del origen de datos** y, después, haga clic en **Conexión incrustada**. Escriba la información requerida.  
  
     En el panel Datos de informe, el icono de origen de datos cambia al icono de origen de datos compartido.  
  
## <a name="see-also"></a>Vea también  
 [Administrar orígenes de datos de informe](../../reporting-services/report-data/manage-report-data-sources.md)   
 [Conexiones de datos, orígenes de datos y cadenas de conexión &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  
  
  
