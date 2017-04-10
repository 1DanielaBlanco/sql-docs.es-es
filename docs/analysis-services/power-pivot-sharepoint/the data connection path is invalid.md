---
title: "La ruta de acceso de la conexi&#243;n de datos en el libro se&#241;ala a un archivo en la unidad local o es un URI no v&#225;lido. No se pudieron actualizar las siguientes conexiones: datos PowerPivot | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: bd22e41a-0931-4d32-888a-633a3046fc5e
caps.latest.revision: 7
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# La ruta de acceso de la conexi&#243;n de datos en el libro se&#241;ala a un archivo en la unidad local o es un URI no v&#225;lido. No se pudieron actualizar las siguientes conexiones: datos PowerPivot
  En los libros de Excel que contienen datos [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , Excel Services devuelve este error si no puede conectarse a orígenes de datos insertados.  
  
## Detalles  
  
|||  
|-|-|  
|Se aplica a|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint|  
|Versión del producto|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Causa|Excel Services se configura para permitir únicamente las conexiones de datos de archivos .odc que estén en una biblioteca de conexiones de datos de confianza.|  
|Texto del mensaje|La ruta de acceso de la conexión de datos en el libro señala a un archivo en la unidad local o es un URI no válido. No se pudieron actualizar las siguientes conexiones: datos [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]|  
  
## Explicación  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] contienen conexiones de datos insertados. Para admitir la interacción de los libros a través de segmentaciones y filtros, Servicios de Excel se debe configurar para permitir el acceso de datos externos a través de la información de las conexiones incrustadas. Se requiere acceso a los datos externos para recuperar los datos [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] que se cargan en los servidores [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] de la granja.  
  
## Acción del usuario  
 Cambie la configuración para permitir conexiones a orígenes de datos incrustados.  
  
1.  En Administración central, en Administración de aplicaciones, haga clic en **Administrar aplicaciones de servicio**.  
  
2.  Haga clic en **Aplicación de Servicios de Excel**.  
  
3.  Haga clic en **Ubicación de archivo de confianza**.  
  
4.  Haga clic en **http://** o en la ubicación que quiera configurar.  
  
5.  En Datos externos, en Permitir datos externos, haga clic en **Bibliotecas de conexiones de datos de confianza e incrustadas**.  
  
6.  Haga clic en **Aceptar**.  
  
 O bien, puede crear una nueva ubicación de confianza para los sitios que contienen los libros [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] y, a continuación, modificar la configuración solo para ese sitio. Para más información, vea [Create a trusted location for Power Pivot sites in Central Administration](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
  