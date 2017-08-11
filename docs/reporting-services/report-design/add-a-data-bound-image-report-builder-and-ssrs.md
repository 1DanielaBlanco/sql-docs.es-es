---
title: Agregar una imagen enlazada a datos (generador de informes y SSRS) | Documentos de Microsoft
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
ms.assetid: df4c38d4-bfcc-41c4-aa6d-952ca6fd7a2e
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 253d3abfffae056d6300e2203623e7af023a2476
ms.contentlocale: es-es
ms.lasthandoff: 08/09/2017

---
# <a name="add-a-data-bound-image-report-builder-and-ssrs"></a>Agregar una imagen enlazada a datos (Generador de informes y SSRS)
  Un informe puede incluir una referencia a una imagen que está almacenada en una base de datos. Este tipo de imagen se conoce como *imagen enlazada a datos*. Las imágenes que aparecen junto a los nombres de producto de una lista de productos son ejemplos de imágenes enlazadas a datos.  
  
 Agregar una imagen enlazada a datos a un encabezado de página o a un pie de página requiere pasos adicionales. Para más información, vea [Encabezados y pies de página &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/page-headers-and-footers-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-data-bound-image"></a>Agregar una imagen enlazada a datos  
  
1.  En la vista de diseño del informe, cree una tabla con una conexión a un origen de datos y un conjunto de datos con un campo que contenga los datos binarios de la imagen. Para más información, vea [Tablas &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/tables-report-builder-and-ssrs.md).  
  
2.  Inserte una columna en la tabla. Para más información, vea [Insertar o eliminar una columna &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/insert-or-delete-a-column-report-builder-and-ssrs.md).  
  
3.  En el menú **Insertar** , haga clic en **Imagen**y, a continuación, haga clic en la fila de datos de la nueva columna.  
  
4.  En la página General del cuadro de diálogo **Propiedades de la imagen** , escriba un nombre en el cuadro de texto **Nombre** o acepte el predeterminado.  
  
5.  (Opcional) En el cuadro de texto **Información sobre herramientas** , escriba el texto que se debe mostrar cuando el usuario mantenga el mouse sobre la imagen en un informe representado para HTML.  
  
6.  En **Seleccionar el origen de la imagen**, seleccione **Base de datos**.  
  
7.  En **Usar este campo**, seleccione el campo que contiene las imágenes en el informe.  
  
8.  En **Usar este tipo MIME**, seleccione el tipo MIME, o el formato de archivo, de la imagen, por ejemplo, bmp.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Aparece un marcador de posición para la imagen en la superficie de diseño del informe.  
  
## <a name="see-also"></a>Vea también  
 [Imágenes &#40; El generador de informes y SSRS &#41;](../../reporting-services/report-design/images-report-builder-and-ssrs.md)   
 [Incrustar una imagen en un informe &#40; El generador de informes y SSRS &#41;](../../reporting-services/report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md)   
 [Agregar una imagen externa &#40; El generador de informes y SSRS &#41;](../../reporting-services/report-design/add-an-external-image-report-builder-and-ssrs.md)   
 [Cuadro de diálogo de propiedades de imagen, General &#40; El generador de informes y SSRS &#41;](http://msdn.microsoft.com/library/c2218b93-f7fe-46ef-995f-d7dadf9752ec)  
  
  
