---
title: "Filter Data before Exporting (MDS Add-in for Excel) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 10
---
# Filter Data before Exporting (MDS Add-in for Excel)
  En [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], filtrar los datos cuando desea limitar el tamaño o el ámbito de los datos que va a exportar a Excel.  
  
## Requisitos previos  
 Para realizar este procedimiento:  
  
-   Debe disponer de permiso de acceso al área funcional **Explorador** .  
  
### Para filtrar los datos antes de exportar  
  
1.  Abra Excel y, en la pestaña **Datos maestros** , conéctese a un repositorio MDS. Para obtener más información, consulte [conectarse a un repositorio MDS & #40; Complemento MDS para Excel y nº 41;](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  En el panel **Explorador de datos maestros** , seleccione un modelo y una versión. La lista de entidades se rellena.  
  
    -   Si el panel **Explorador de datos maestros** no está visible, en el grupo **Conectar y cargar** , haga clic en **Mostrar explorador**.  
  
    -   Si el **Explorador de datos maestros** panel está deshabilitado, es porque la hoja existente ya contiene datos administrados por MDS. Para habilitar el panel, abra una nueva hoja de cálculo.  
  
3.  En el panel **Explorador de datos maestros** , en la lista de entidades, haga clic en la entidad que desea filtrar.  
  
4.  En la cinta de opciones, en el grupo **Conectar y cargar** , haga clic en **Filtro**.  
  
5.  Completar la **filtro** cuadro de diálogo, seleccione los atributos (columnas) para mostrar, establecer el orden de las columnas y, si es necesario, filtrar los datos por lo que se devuelven menos filas. Vea en el panel **Resumen** cuántos datos se devolverán. Para obtener más información, consulte [cuadro de diálogo Filtro & #40; Complemento MDS para Excel y nº 41;](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md).  
  
6.  Haga clic en **Cargar datos**. La hoja se rellena con datos administrados por MDS.  
  
    > [!NOTE]  
    >  -   Solo se carga en Excel el primer millón de miembros.  
    > -   En las columnas que son listas restringidas (atributos basados en dominio), solo se cargan los 25000 primeros valores de forma predeterminada.  
  
## Pasos siguientes  
 [Importar datos de Excel en Master Data Services & #40; Complemento MDS para Excel y nº 41;](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## Vea también  
 [Información general: Exportar datos a Excel y Nº 40; Complemento MDS para Excel y nº 41;](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Cuadro de diálogo Filtro & #40; Complemento MDS para Excel y nº 41;](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md)   
 [Reordenar columnas & #40; Complemento MDS para Excel y nº 41;](../../master-data-services/microsoft-excel-add-in/reorder-columns-mds-add-in-for-excel.md)  
  
  