---
title: Generar fuentes de distribución de datos a partir de un informe (Generador de informes y SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e68baae2-9f2a-4f13-9179-9ac7f29111c5
caps.latest.revision: 8
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 62e0dead34079abbceda90dabca6f44c7dbd5126
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36103983"
---
# <a name="generate-data-feeds-from-a-report-report-builder-and-ssrs"></a>Generar fuentes de distribución de datos a partir de un informe (Generador de informes y SSRS)
  Puede generar fuentes de datos compatibles con Atom a partir de informes y, a continuación, usar las fuentes de distribución de datos en las aplicaciones, como el [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] cliente, que puede consumir fuentes de datos.  
  
 La extensión de representación de Atom de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] genera un documento de servicio de Atom que enumera las fuentes de distribución de datos disponibles en un informe. El documento enumera al menos una fuente de distribución de datos para cada región de datos del informe. Según el tipo de región de datos y los datos que esta muestra, [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] podría generar varias fuentes de distribución de datos a partir de una región de datos.  
  
 El documento de servicio de Atom contiene un identificador único para cada una de las fuentes de distribución de datos que se usa en una dirección URL para ver el contenido de la fuente de distribución de datos.  
  
 Para obtener más información, vea [Generating Data Feeds from Reports &#40;Report Builder and SSRS&#41;](generating-data-feeds-from-reports-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-generate-an-atom-service-document"></a>Generar un documento de servicio de Atom  
  
1.  En la página **Inicio** del Administrador de informes, navegue hasta el informe con el que desea generar las fuentes de distribución de datos.  
  
2.  Haga clic en el informe.  
  
     El informe se ejecuta.  
  
3.  En la barra de herramientas, haga clic en el icono Exportar a fuente de distribución de datos.  
  
     Aparece un mensaje en el que se pregunta si desea guardar o abrir el documento de Atom que contiene la fuente de distribución de datos.  
  
4.  Haga clic en **Guardar** para guardar el documento en el sistema de archivos o en **Abrir** para ver el contenido del documento antes de guardarlo. **De forma predeterminada, el documento se abre en un explorador.**  
  
5.  Busque la ubicación para guardar el documento.  
  
6.  Si lo desea, cambie el nombre del documento.  
  
    > [!NOTE]  
    >  De manera predeterminada, el nombre del documento es el del informe.  
  
7.  Compruebe que el tipo de documento es **Archivo ATOMSVC**y, a continuación, haga clic en **Guardar**.  
  
8.  Si lo desea, abra el archivo .atomsvc en un explorador o un editor de texto o XML.  
  
### <a name="to-view-an-atom-compliant-data-feed"></a>Ver una fuente de distribución de datos conforme a Atom  
  
1.  Si el documento de servicio de Atom no está abierto aún, búsquelo y ábralo en un explorador como Internet Explorer.  
  
2.  Copie la dirección URL de la fuente de distribución de datos que desea ver del documento de servicio de Atom al explorador.  
  
     El formato de la dirección URL es el siguiente:  
  
 `http://<server name>/ReportServer?%2f<ReportName>rs%3aCommand=Render&rs%3aFormat=ATOM&rc%3aDataFeed=<Identifier>`  
  
1.  Presione ENTRAR.  
  
     Aparece un mensaje en el que se pregunta si desea guardar o abrir el documento de Atom que contiene la fuente de distribución de datos.  
  
2.  Haga clic en **Guardar** para guardar el documento en el sistema de archivos, o en **Abrir** para ver la fuente de distribución de datos antes de guardar.  
  
3.  Busque la ubicación para guardar el documento.  
  
4.  Si lo desea, cambie el nombre del documento.  
  
    > [!NOTE]  
    >  De forma predeterminada, el nombre del documento es el del informe. Si el documento de servicio de Atom tiene varias fuentes, de forma predeterminada todas usas el mismo nombre, el del informe. Para diferenciarlas, cambie su nombre por otro descriptivo.  
  
5.  Compruebe que el tipo de documento es **Archivo ATOM**y, a continuación, haga clic en **Guardar**.  
  
6.  Si lo desea, abra el archivo .atom en un explorador o editor de texto o XML.  
  
## <a name="see-also"></a>Vea también  
 [Exportar informes &#40;el generador de informes SSRS&#41;](export-reports-report-builder-and-ssrs.md)  
  
  