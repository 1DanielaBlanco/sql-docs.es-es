---
title: Cómo implementar un elemento de informe personalizado | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- custom report items, deploying
ms.assetid: 80e97b0d-e355-4240-aebd-08cbc84089ed
caps.latest.revision: 25
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c65d3a2f3fd26fd87c8471676d68a052126c542c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36197553"
---
# <a name="how-to-deploy-a-custom-report-item"></a>Cómo implementar un elemento de informe personalizado
  Para implementar un elemento de informe personalizado en [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], debe modificar los archivos de configuración del servidor de informes y copiar los ensamblados de componentes en tiempo de diseño y en tiempo de ejecución a las carpetas de aplicación correspondientes para el Diseñador de informes y el servidor de informes.  
  
### <a name="to-deploy-a-custom-report-item"></a>Para implementar un elemento de informe personalizado  
  
1.  Modifique el archivo Rsreportdesigner.config para configurar los componentes de tiempo de ejecución y de tiempo de diseño de elementos de informe personalizados que se utilizarán en el diseñador. Observe que la entrada `ReportItemName` debe coincidir con el atributo `CustomReportItemAttribute` utilizado en la clase `CustomReportItemDesigner`. Por ejemplo:  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    <ReportItemDesigner>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsDesigner, PolygonsDesigner" />  
    </ReportItemDesigner>  
    <ReportItemConverter>  
       <Converter Source="Chart" Target="Polygons" Type="PolygonsCRI.PolygonsConverter, PolygonsDesigner" />  
    </ReportItemConverter>  
    ```  
  
2.  Modifique el archivo Rsreportserver.config para registrar el componente de tiempo de ejecución del elemento de informe personalizado. Por ejemplo:  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    ```  
  
3.  Modifique el archivo Rsssrvpolicy.config para agregar un `CodeGroup` que conceda los permisos apropiados al elemento de informe personalizado. Por ejemplo:  
  
    ```  
    <CodeGroup   
       class="UnionCodeGroup"   
       version="1"   
       PermissionSetName="FullTrust"  
       Description="This code group grants MyCustomReportItem.dll FullTrust permission. ">  
       <IMembershipCondition   
          class="UrlMembershipCondition"  
          version="1"  
       Url="C:\Program Files\Microsoft SQL Server\ MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin\MyCustomReportItem.dll" />  
    </CodeGroup>  
    ```  
  
4.  Copie el DLL de componente de tiempo de ejecución del elemento de informe en los directorios \Archivos de programa\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies y %Archivos de programa%\Microsoft SQL Server\MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin.  
  
5.  Copie el DLL de componente de tiempo de diseño de elemento de informe en el directorio %Archivos de programa%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.  
  
## <a name="see-also"></a>Vea también  
 [Archivos de configuración de Reporting Services](../report-server/reporting-services-configuration-files.md)   
 [Bibliotecas de clases de elemento de informe personalizado](custom-report-item-class-libraries.md)  
  
  