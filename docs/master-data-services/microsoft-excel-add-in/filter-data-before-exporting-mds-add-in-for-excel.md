---
title: Filtrar los datos antes de exportar (complemento MDS para Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.service: ''
ms.component: microsoft-excel-add-in
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
caps.latest.revision: 10
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 957923869599d5b62963abe94e141184e4c8baa4
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="filter-data-before-exporting-mds-add-in-for-excel"></a>Filtrar los datos antes de exportar (complemento MDS para Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  En [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] puede filtrar los datos si desea limitar el tamaño o el ámbito de los datos que va a exportar a Excel.  
  
## <a name="prerequisites"></a>Prerequisites  
 Para realizar este procedimiento:  
  
-   Debe disponer de permiso de acceso al área funcional **Explorador** .  
  
### <a name="to-filter-data-before-exporting"></a>Para filtrar los datos antes de exportarlos  
  
1.  Abra Excel y, en la pestaña **Datos maestros** , conéctese a un repositorio MDS. Para obtener más información, consulte [Conectarse a un repositorio MDS &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  En el panel **Explorador de datos maestros** , seleccione un modelo y una versión. La lista de entidades se rellena.  
  
    -   Si el panel **Explorador de datos maestros** no está visible, en el grupo **Conectar y cargar** , haga clic en **Mostrar explorador**.  
  
    -   Si el panel **Explorador de datos maestros** está deshabilitado, se debe a que la hoja existente ya contiene datos administrados por MDS. Para habilitar el panel, abra una nueva hoja de cálculo.  
  
3.  En el panel **Explorador de datos maestros** , en la lista de entidades, haga clic en la entidad que desea filtrar.  
  
4.  En la cinta de opciones, en el grupo **Conectar y cargar** , haga clic en **Filtro**.  
  
5.  Para completar el cuadro de diálogo **Filtro** , seleccione los atributos (columnas) para mostrar, establecer el orden de las columnas y, si es necesario, filtrar los datos de modo que se devuelvan menos filas. Vea en el panel **Resumen** cuántos datos se devolverán. Para más información, vea [Cuadro de diálogo Filtrar &#40;Complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md).  
  
6.  Haga clic en **Cargar datos**. La hoja se rellena con datos administrados por MDS.  
  
    > [!NOTE]  
    >  -   Solo se carga en Excel el primer millón de miembros.  
    > -   En las columnas que son listas restringidas (atributos basados en dominio), solo se cargan los 25000 primeros valores de forma predeterminada.  
  
## <a name="next-steps"></a>Next Steps  
 [Importación de datos de Excel en Master Data Services &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>Ver también  
 [Información general: Exportar datos a Excel &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Cuadro de diálogo Filtrar &#40;Complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md)   
 [Reordenar columnas &#40;complemento MDS para Excel&#41;](../../master-data-services/microsoft-excel-add-in/reorder-columns-mds-add-in-for-excel.md)  
  
  
