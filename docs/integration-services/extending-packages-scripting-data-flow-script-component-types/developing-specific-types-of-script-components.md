---
title: "Desarrollar tipos específicos de los componentes de Script | Documentos de Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: dfbbe959-6b4e-4b47-b9dd-bcc31929482d
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 458ba4be689ed976a5948380d35f38020f7dd4dd
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="developing-specific-types-of-script-components"></a>Desarrollar tipos específicos de los componentes de script
  El componente de script es una herramienta configurable que puede utilizar en el flujo de los datos de un paquete para llenar casi cualquier requisito no cumplido por los orígenes, transformaciones y destinos que se incluyen con [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Esta sección contiene ejemplos de código de componente de script que muestran las cuatro opciones para configurar el componente de script:  
  
-   Como un origen.  
  
-   Como una transformación con salidas sincrónicas.  
  
-   Como una transformación con salidas asincrónicas.  
  
-   Como un destino.  
  
 Para obtener ejemplos adicionales del componente de Script, consulte [Additional Script Component Examples](../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Crear un origen con el componente de script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-source-with-the-script-component.md)  
 Explica y muestra cómo crear un origen de flujo de datos mediante el componente de script.  
  
 [Crear una transformación sincrónica con el componente de script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)  
 Explica y muestra cómo crear una transformación de flujo de datos con salidas sincrónicas mediante el componente de script. Este tipo de transformación modifica filas de datos en su lugar cuando pasan a través del componente.  
  
 [Crear una transformación asincrónica con el componente de script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)  
 Explica y muestra cómo crear una transformación de flujo de datos con salidas asincrónicas mediante el componente de script. Este tipo de transformación tiene que leer todas las filas de datos antes de poder agregar más información, como agregados calculados, a los datos que pasan a través del componente.  
  
 [Crear un destino con el componente de script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
 Explica y muestra cómo crear un destino de flujo de datos mediante el componente de script.  
  
## <a name="see-also"></a>Vea también  
 [Comparar soluciones de Scripting y objetos personalizados](../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)   
 [Componentes de flujo de desarrollar tipos específicos de datos](../../integration-services/extending-packages-custom-objects-data-flow-types/developing-specific-types-of-data-flow-components.md)  
  
  
