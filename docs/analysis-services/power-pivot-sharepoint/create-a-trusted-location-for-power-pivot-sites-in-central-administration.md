---
title: "Crear una ubicaci&#243;n de confianza para los sitios PowerPivot en Administraci&#243;n central | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a666f365-cd93-43a3-9d3d-e429dfc19b66
caps.latest.revision: 8
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 7
---
# Crear una ubicaci&#243;n de confianza para los sitios PowerPivot en Administraci&#243;n central
  Servicios de Excel permite especificar qué ubicaciones son repositorios válidos para los libros que se abren en un servidor de SharePoint. Estas ubicaciones se denominan 'ubicaciones de confianza' y puede utilizar opciones de configuración diferentes para cada ubicación de confianza que cree. En una implementación de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint, podría considerar crear una ubicación de confianza para los sitios que contienen libros [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , de modo que pueda aplicar la configuración que funcione mejor para acceder a datos [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , al tiempo que conserva la configuración predeterminada para el resto de la granja.  
  
 Este tema contiene las siguientes secciones:  
  
 [Requisitos previos](#prereq)  
  
 [Información general](#overview)  
  
 [Crear una ubicación de confianza para acceso a datos PowerPivot](#create)  
  
## Requisitos previos  
 Debe ser administrador de servicios o de una granja para designar una dirección URL como una ubicación de confianza.  
  
 Debe conocer la dirección URL del sitio de SharePoint que contiene la Galería de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] u otra biblioteca que almacene los libros. Para obtener la dirección, abra el sitio que contenga la biblioteca, haga clic con el botón derecho en **Galería de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]**, seleccione **Propiedades** y, después, copie la primera parte de la dirección (URL) que contiene el nombre del servidor y la ruta de acceso al sitio.  
  
##  <a name="overview"></a> Información general  
 Una instalación inicial de Servicios de Excel especifica 'http://' como su ubicación de confianza, lo que significa que los libros de cualquier sitio de la granja se pueden abrir en el servidor. Si requiere un control más estrecho sobre las ubicaciones que se consideren de confianza, puede crear nuevas ubicaciones de confianza que se asignen a sitios concretos de una granja y, a continuación, variar la configuración y los permisos de cada una.  
  
 Crear una nueva ubicación de confianza para los sitios que hospedan los libros [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] es especialmente útil si desea conservar los valores predeterminados para el resto de la granja, mientras aplica valores diferentes que funcionan mejor para el acceso a datos [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Por ejemplo, una ubicación de confianza que esté optimizada para los libros [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] podría tener un tamaño de libro máximo de 50 MB, mientras que el resto de la granja utiliza el valor predeterminado de 10 MB.  
  
 Se recomienda crear una ubicación de confianza si está utilizando las bibliotecas de la Galería de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para ofrecer una vista previa de los libros publicados y encuentra advertencias en la actualización de datos en lugar de la imagen de la vista previa que esperaba. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] representa imágenes en miniatura de los informes y los libros utilizando los datos y la información de la presentación dentro del documento. Si la opción Warn on Data Refresh (Avisar al actualizar datos) está habilitada para una ubicación de confianza, la Galería de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] podría no tener los permisos necesarios para realizar la actualización, con lo que aparecería un error en lugar de la imagen en miniatura. Si se agrega un sitio que contiene la Galería de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] como una nueva ubicación de confianza, es posible que se elimine este problema.  
  
##  <a name="create"></a> Crear una ubicación de confianza para acceso a datos PowerPivot  
  
1.  En Administración central, en Administración de aplicaciones, haga clic en **Administrar aplicaciones de servicio**.  
  
2.  Haga clic en la aplicación de servicio de Servicios de Excel.  
  
3.  Haga clic en **Ubicaciones de archivos de confianza**.  
  
4.  Haga clic en **Agregar ubicación de archivo de confianza**.  
  
5.  Escriba la dirección URL de un sitio que contenga una biblioteca de la Galería de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
6.  En Tipo de ubicación, seleccione **Microsoft SharePoint Foundation**.  
  
    > [!IMPORTANT]  
    >  Los tipos de ubicación HTTP y UNC no se admiten para el acceso a datos [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].  
  
7.  Acepte toda la configuración predeterminada para las propiedades de Administración de sesiones, Propiedades del libro y Comportamiento del cálculo.  
  
8.  En Propiedades del libro, establezca **Tamaño máximo del libro** en **50**. De esta forma, se alinea el límite superior del tamaño de archivo al límite superior para las cargas de archivo en la aplicación del sitio web principal. Si los libros son mayores de 50 megabytes, debe aumentar el límite del tamaño de archivo. Para más información, vea [Configuración del tamaño de carga máximo de archivos &#40;PowerPivot para SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/configure-maximum-file-upload-size-power-pivot-for-sharepoint.md).  
  
9. En Datos externos, compruebe que Permitir datos externos está establecido en **Bibliotecas de conexiones de datos de confianza e incrustadas**. Este valor se requiere para acceder a datos [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] en un libro.  
  
10. Además, en Datos externos, en Avisar al actualizar, desactive la casilla de **Advertencia de actualización habilitada**. Al desactivar la casilla, se permite que la Galería de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] omita los mensajes de advertencia rutinarios y muestre imágenes de vista previa de un libro en su lugar.  
  
11. Haga clic en **Aceptar**.  
  
## Vea también  
 [Galería de PowerPivot](../Topic/Power%20Pivot%20Gallery.md)   
 [Creación y personalización de la Galería de PowerPivot](../../analysis-services/power-pivot-sharepoint/create-and-customize-power-pivot-gallery.md)   
 [Uso de la Galería de Power Pivot](../../analysis-services/power-pivot-sharepoint/use-power-pivot-gallery.md)  
  
  