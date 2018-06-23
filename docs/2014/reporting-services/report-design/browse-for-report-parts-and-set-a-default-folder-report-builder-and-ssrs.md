---
title: Buscar elementos de informe y establecer una carpeta predeterminada (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5cf38068-65d1-4fe8-81f3-a404d8fbc663
caps.latest.revision: 5
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: e16f84d38d32dc5e55ce3244f09b2e9c5a28f967
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36103256"
---
# <a name="browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs"></a>Buscar elementos de informe y establecer una carpeta predeterminada (Generador de informes y SSRS)
  La manera más fácil de crear un informe es agregarle elementos, como tablas y gráficos, de la galería de elementos de informe. Al agregar un elemento de informe al informe, también agrega todo lo que debe tener para que funcione. Por ejemplo, cualquier elemento de informe que muestre los datos depende de un conjunto de datos, es decir, una consulta y una conexión a un origen de datos. Después de agregar el elemento de informe a un informe, puede modificarlo como convenga.  
  
 Puede establecer una carpeta predeterminada para publicar elementos de informe en el servidor de informes o el sitio de SharePoint integrado con un servidor de informes.  
  
 Para más información, vea [Report Parts &#40;Report Builder and SSRS&#41;](../report-parts-report-builder-and-ssrs.md).  
  
### <a name="to-browse-for-report-parts"></a>Para buscar elementos de informe  
  
1.  En el menú **Insertar** , haga clic en **Elementos de informe**.  
  
     Si no está conectado, haga clic en **Conectar con un servidor de informes**y escriba el nombre.  
  
    > [!NOTE]  
    >  Debe estar conectado a un servidor de informes para buscar elementos de informe.  
  
2.  Puede restringir la búsqueda especificando detalles sobre el elemento de informe. Escriba todo o parte del nombre y la descripción en el cuadro **Buscar** , o haga clic **Agregar criterios** y agregue los valores para alguno de los campos o para todos:  
  
    -   Creado por  
  
    -   Fecha de creación  
  
    -   Fecha de última modificación  
  
    -   Última modificación por  
  
    -   Carpeta del servidor  
  
    -   Tipo  
  
     Por ejemplo, para encontrar una imagen, haga clic en **Agregar criterios**y, a continuación, haga clic en **Tipo**. En la lista desplegable, active la casilla **Imagen** , presione ENTRAR y, a continuación, haga clic en la lupa de Buscar.  
  
    > [!NOTE]  
    >  Para los valores de **Creado por** y **Última modificación por** , busque el nombre de usuario de la persona como se representa en el servidor de informes.  
  
### <a name="to-set-a-default-folder-for-report-parts"></a>Para establecer una carpeta predeterminada para elementos de informe  
  
1.  Haga clic en **Generador de informes**y, a continuación, en **Opciones**.  
  
2.  En el cuadro de diálogo **Opciones** , en la pestaña **Configuración** , escriba un nombre de carpeta en el cuadro de texto **Publicar elementos de informe en esta carpeta de forma predeterminada** .  
  
 El Generador de informes creará esta carpeta si se dispone de permisos para crear carpetas en el servidor de informes y la carpeta no existe todavía.  
  
 No necesita reiniciar el Generador de informes para que esta configuración surta efecto.  
  
## <a name="see-also"></a>Vea también  
 [Busque actualizaciones o Turn Off &#40;el generador de informes SSRS&#41;](../check-for-updates-or-turn-updates-off-report-builder-and-ssrs.md)   
 [Elementos de informe &#40;el generador de informes SSRS&#41;](../report-parts-report-builder-and-ssrs.md)   
 [Elementos de informe y conjuntos de datos en el generador de informes](../report-data/report-parts-and-datasets-in-report-builder.md)   
 [Solucionar problemas de elementos de informe &#40;el generador de informes SSRS&#41;](../troubleshoot-report-parts-report-builder-and-ssrs.md)   
 [Publicar y volver a publicar elementos de informe &#40;el generador de informes SSRS&#41;](publish-and-republish-report-parts-report-builder-and-ssrs.md)  
  
  