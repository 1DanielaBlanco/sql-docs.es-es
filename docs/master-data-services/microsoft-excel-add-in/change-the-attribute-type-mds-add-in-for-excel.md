---
title: "Cambar el tipo de atributo (complemento MDS para Excel) | Microsoft Docs"
ms.custom: ""
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9d3001d9-8d0f-4e4a-8e04-4f666bf0df69
caps.latest.revision: 8
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 8
---
# Cambar el tipo de atributo (complemento MDS para Excel)
  En el [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], los administradores pueden cambiar el tipo de atributo cuando el tipo de datos o el número de caracteres permitido sea incorrecto.  
  
 Si quiere cambiar el tipo de atributo para crear una lista restringida (atributo basado en dominios), consulte [Crear un atributo basado en dominio &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/create-a-domain-based-attribute-mds-add-in-for-excel.md).  
  
> [!NOTE]  
>  No se puede actualizar el tipo o la longitud de las columnas **Nombre** o **Código**.  
  
## Requisitos previos  
 Para realizar este procedimiento:  
  
-   Debe disponer del permiso para tener acceso a las áreas funcionales del **Explorador** y de **Administración del sistema** .  
  
-   Debe ser administrador de modelo. Para obtener más información, vea [Administradores &#40;Master Data Services&#41;](../../master-data-services/administrators-master-data-services.md).  
  
-   Debe haber un modelo, una entidad y un atributo existentes.  
  
### Para cambiar el tipo de atributo  
  
1.  En Excel, cargue la entidad que contenga la columna (atributo) que desee cambiar. Para obtener más información, consulte [Exportar datos a Excel desde Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md).  
  
2.  Haga clic en cualquier celda en la columna que desee cambiar.  
  
3.  En el grupo **Compilar modelo** , haga clic en **Propiedades de atributo**.  
  
4.  En el cuadro de diálogo **Propiedades de atributo** , actualice los valores según sea necesario.  
  
5.  Haga clic en **Aceptar**.  
  
## ¿Qué ocurre cuando se cambia el tipo de atributo?  
 Si hay alguna dependencia del atributo, como, por ejemplo, que una jerarquía derivada o una regla de negocio de MDS haga referencia al atributo, no puede cambiar el tipo de datos del atributo. Obtendrá un error que indica que el tipo de atributo no se puede modificar porque un objeto hace referencia a él.  
  
 Si hay algún error durante la conversión de tipos de datos para los valores de atributo, MDS hace lo siguiente.  
  
-   Cambia el tipo de datos del atributo.  
  
-   Generar una copia del atributo con el sufijo "_old" que contiene los valores anteriores. Se le denomina atributo desusado.  
  
## Vea también  
 [Atributos &#40;Master Data Services&#41;](../../master-data-services/attributes-master-data-services.md)   
 [Generar un modelo &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/building-a-model-mds-add-in-for-excel.md)  
  
  