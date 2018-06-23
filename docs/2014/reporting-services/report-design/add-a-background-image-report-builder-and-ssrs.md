---
title: Agregar una imagen de fondo (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c777fefb-8695-44a7-b5cd-a18c587583f2
caps.latest.revision: 9
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 278a4c2a420a499a1743caab74e61659caa18515
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36200856"
---
# <a name="add-a-background-image-report-builder-and-ssrs"></a>Agregar una imagen de fondo (Generador de informes y SSRS)
  Puede agregar una imagen de fondo a un elemento del informe, como un rectángulo, cuadro de texto, lista, matriz, tabla y algunas partes de un gráfico; o a una sección del informe, como el encabezado de página, el pie de página o el cuerpo del informe. Puede definir una imagen de fondo para cualquier elemento seleccionado en la superficie de diseño del informe que muestre **BackgroundImage** en el panel de propiedades. Al igual que otras imágenes, la imagen de fondo puede ser una dirección URL a una imagen del servidor de informes, a una imagen de un campo de conjunto de datos o a una imagen incrustada en la definición de informe. Para usar una imagen incrustada en el informe, primero debe agregar la imagen a la definición de informe, antes de agregarla a la superficie de diseño.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-embed-an-image-in-the-report-definition"></a>Incrustar una imagen en la definición de informe  
  
1.  En el panel Datos de informe, haga clic con el botón derecho en el nodo **Imágenes** y, después, haga clic en **Agregar imagen**.  
  
    > [!NOTE]  
    >  Si el panel Datos de informe no está visible, haga clic en **Datos de informe** en la pestaña **Ver**.  
  
2.  Navegue hasta la imagen que desea incrustar en la definición de informe y, a continuación, haga clic en **Aceptar**.  
  
### <a name="to-add-a-background-image"></a>Agregar una imagen de fondo  
  
1.  En la vista de diseño del informe, seleccione el elemento de informe al que desea agregar una imagen de fondo.  
  
2.  Si el panel de propiedades no está visible, en la pestaña **Ver** , seleccione **Propiedades**.  
  
3.  En el panel de propiedades, expanda **BackgroundImage**y haga lo siguiente:  
  
    -   Para una imagen incrustada:  
  
         Establezca **Origen** en **Incrustada**.  
  
         Establezca **Valor** en el nombre de una imagen que esté incrustada en el informe.  
  
    -   Para una imagen externa:  
  
         Establezca **Origen** en **Externo**.  
  
         Establezca **Valor** en una ruta de acceso válida a una imagen. Puede tratarse de un servidor de informes en modo nativo o en modo integrado de SharePoint, o puede ser cualquier otro sitio web. Para más información, vea [Agregar una imagen externa &#40;Generador de informes y SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md).  
  
    -   Para una imagen que esté contenida en un campo en la base de datos a la que está conectado el elemento de informe:  
  
         Establezca **Origen** en **Base de datos**.  
  
         Establezca **Valor** en el nombre de un campo en el conjunto de datos de informe. Para más información, vea [Agregar una imagen enlazada a datos &#40;Generador de informes y SSRS&#41;](add-a-data-bound-image-report-builder-and-ssrs.md).  
  
         En **MIMEType**, o el formato de archivo, seleccione el tipo MIME que corresponda a la imagen, por ejemplo, .bmp.  
  
        > [!NOTE]  
        >  MIMEType solamente se aplica si la propiedad **Origen** se establece en **Base de datos**. Si la propiedad **Source** se establece como **External** o **Embedded**, el valor de **MIMEType** no se tiene en cuenta.  
  
    -   Para **BackgroundRepeat**, seleccione una expresión, **Default**, **Repeat**, **RepeatX**, o **RepeatY**o **Clip**.  
  
         Para las imágenes de fondo en los gráficos, **BackgroundRepeat** se puede establecer en **Default**, **Repeat**, **Fit**y **Clip**, pero no en **RepeatX** ni **RepeatY**.  
  
## <a name="see-also"></a>Vea también  
 [Imágenes &#40;el generador de informes SSRS&#41;](images-report-builder-and-ssrs.md)   
 [Cuadro de diálogo de Propiedades de la imagen, General &#40;Generador de informes y SSRS&#41;](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  