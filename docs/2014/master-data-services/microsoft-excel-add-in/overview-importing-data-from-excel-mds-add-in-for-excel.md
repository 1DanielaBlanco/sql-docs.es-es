---
title: Publicación de datos (complemento MDS para Excel) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ea84a9aa-aeec-411b-ab8d-bc1b14f864a3
caps.latest.revision: 8
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: f9fbee4ad70222c81f8f2fc40c460974f6f5ac05
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37155066"
---
# <a name="publishing-data-mds-add-in-for-excel"></a>Publicar datos (complemento MDS para Excel)
  En [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], puede publicar los datos en el repositorio MDS si desea compartirlo con otros usuarios. En cuanto se publiquen los datos, estarán disponibles para otros usuarios del complemento para su descarga.  
  
 Al publicar datos, todos los que haya agregado o actualizado se publican en el repositorio MDS. Los datos que ha eliminado no se publican y se deben eliminar por separado. Para obtener más información, consulte [Delete a Row &#40;MDS Add-in for Excel&#41;](delete-a-row-mds-add-in-for-excel.md).  
  
> [!NOTE]  
>  La publicación no se puede usar para crear una entidad nueva. Para obtener más información sobre cómo crear entidades, consulte [Crear una entidad &#40;Complemento MDS para Excel&#41;](create-an-entity-mds-add-in-for-excel.md).  
  
## <a name="when-multiple-users-publish-at-the-same-time"></a>Cuando varios usuarios publican simultáneamente  
 Varios usuarios pueden publicar actualizaciones de los mismos datos. A medida que cada usuario publica, la actualización se guarda en la base de datos. Esto significa que un usuario que no estaba trabajando con los datos actualizados más recientemente podrá cambiar el valor cuando los publique.  
  
 Solo las actualizaciones que se realizan se publican en la base de datos. Los datos obsoletos de la hoja de cálculo no se publican.  
  
## <a name="transactions-and-annotations"></a>Transacciones y anotaciones  
 Cada cambio publicado se guarda como una transacción. Si lo desea, puede agregar anotaciones (comentarios) a una transacción para explicar por qué se realizó el cambio.  
  
-   No puede anotar las eliminaciones, aunque se guardan como transacciones que un administrador puede invertir.  
  
-   Si cambia el **código** valor para un miembro, no se registra como una transacción y todas las transacciones anteriores para el miembro no están disponibles.  
  
-   Puede ver las transacciones realizadas por otros usuarios en un miembro. También puede ver todas las transacciones que ha realizado en un miembro, aunque ya no tenga permiso para los atributos concretos.  
  
 Puede ver todas las transacciones realizadas en un miembro. Para obtener más información, consulte [View All Annotations or Transactions for a Member &#40;MDS Add-in for Excel&#41;](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md).  
  
> [!IMPORTANT]  
>  Si especifica una anotación de más de 500 caracteres, se trunca automáticamente.  
  
## <a name="business-rule-and-other-validation"></a>Regla de negocios y otras validaciones  
 Al publicar datos, se realiza la validación para asegurarse de que los datos son precisos antes de agregarlos al repositorio MDS. Si los datos no cumplen los criterios especificados, no se publicarán en el repositorio. Para obtener más información, consulte [Validar datos &#40;complemento MDS para Excel&#41;](validating-data-mds-add-in-for-excel.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Descripción de la tarea|Tema|  
|----------------------|-----------|  
|Publicar de nuevo los datos de la hoja de cálculo activa en el repositorio MDS.|[Publicar datos de Excel en MDS &#40;complemento MDS para Excel&#41;](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)|  
|Eliminar una fila del repositorio MDS y de la hoja de cálculo al mismo tiempo.|[Eliminar una fila &#40;complemento MDS para Excel&#41;](delete-a-row-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>Contenido relacionado  
  
-   [Actualizar datos &#40;complemento MDS para Excel&#41;](refreshing-data-mds-add-in-for-excel.md)  
  
-   [Complemento de Master Data Services para Microsoft Excel](master-data-services-add-in-for-microsoft-excel.md)  
  
  
