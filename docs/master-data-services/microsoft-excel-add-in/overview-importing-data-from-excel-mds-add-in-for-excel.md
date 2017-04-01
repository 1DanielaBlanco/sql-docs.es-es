---
title: "Informaci&#243;n general: Importaci&#243;n de datos desde Excel (complemento MDS para Excel) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea84a9aa-aeec-411b-ab8d-bc1b14f864a3
caps.latest.revision: 13
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 11
---
# Informaci&#243;n general: Importaci&#243;n de datos desde Excel (complemento MDS para Excel)
  En [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], puede publicar los datos en el repositorio MDS si desea compartirlo con otros usuarios. En cuanto se publiquen los datos, estarán disponibles para otros usuarios del complemento para su descarga.  
  
 Al publicar datos, todos los que haya agregado o actualizado se publican en el repositorio MDS. Los datos que ha eliminado no se publican y se deben eliminar por separado. Para obtener más información, consulte [Eliminar una fila &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/delete-a-row-mds-add-in-for-excel.md).  
  
> [!NOTE]  
>  La publicación no se puede usar para crear una entidad nueva. Para obtener más información sobre cómo crear entidades, consulte [Crear una entidad &#40;Complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/create-an-entity-mds-add-in-for-excel.md).  
  
## Cuando varios usuarios publican simultáneamente  
 Varios usuarios pueden publicar actualizaciones de los mismos datos. A medida que cada usuario publica, la actualización se guarda en la base de datos. Esto significa que un usuario que no estaba trabajando con los datos actualizados más recientemente podrá cambiar el valor cuando los publique.  
  
 Solo las actualizaciones que se realizan se publican en la base de datos. Los datos obsoletos de la hoja de cálculo no se publican.  
  
## Transacciones y anotaciones  
 Cada cambio publicado se guarda como una transacción. Si lo desea, puede agregar anotaciones (comentarios) a una transacción para explicar por qué se realizó el cambio.  
  
-   No puede anotar las eliminaciones, aunque se guardan como transacciones que un administrador puede invertir.  
  
-   Si cambia el valor de **Code** de un miembro, todas las transacciones anteriores del miembro pasarán a ser no disponibles. Si se devuelve el valor de **Code** al valor original, podrá obtener acceso a las transacciones anteriores.  
  
-   Puede ver las transacciones realizadas por otros usuarios en un miembro. También puede ver todas las transacciones que ha realizado en un miembro, aunque ya no tenga permiso para los atributos concretos. No se pueden ver las transacciones que implican atributos en los que su permiso esté establecido en denegar.  
  
 Puede ver todas las transacciones realizadas en un miembro. Para obtener más información, consulte [Ver todas las anotaciones o transacciones de un miembro &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md).  
  
> [!IMPORTANT]  
>  Si especifica una anotación de más de 500 caracteres, se trunca automáticamente.  
  
## Regla de negocios y otras validaciones  
 Al publicar datos, se realiza la validación para asegurarse de que los datos son precisos antes de agregarlos al repositorio MDS. Si los datos no cumplen los criterios especificados, no se publicarán en el repositorio. Para obtener más información, consulte [Validar datos &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/validating-data-mds-add-in-for-excel.md).  
  
## Tareas relacionadas  
  
|Descripción de la tarea|Tema|  
|----------------------|-----------|  
|Publicar de nuevo los datos de la hoja de cálculo activa en el repositorio MDS.|[Importación de datos de Excel en Master Data Services &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)|  
|Eliminar una fila del repositorio MDS y de la hoja de cálculo al mismo tiempo.|[Eliminar una fila &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/delete-a-row-mds-add-in-for-excel.md)|  
|Vea las anotaciones (comentarios) y las transacciones de las filas de datos (miembros) cuando desee ver actualizaciones de los datos a través del tiempo.|[Ver todas las anotaciones o transacciones de un miembro &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)|  
|Combine los datos de dos hojas de cálculo si desea comparar los datos antes de publicarlos.|[Combinar datos &#40;Complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/combine-data-mds-add-in-for-excel.md)|  
|Solucione los conflictos de combinación para poder publicar los cambios.|[Conflictos de combinación &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/merge-conflicts-mds-add-in-for-excel.md)|  
  
## Contenido relacionado  
  
-   [Actualizar datos &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/refreshing-data-mds-add-in-for-excel.md)  
  
-   [Complemento Master Data Services para Microsoft Excel](../../master-data-services/microsoft-excel-add-in/master-data-services-add-in-for-microsoft-excel.md)  
  
  