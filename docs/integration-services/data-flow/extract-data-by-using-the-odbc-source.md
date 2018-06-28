---
title: Extraer datos mediante el origen de ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 10f25703-49a2-4d45-abab-6b4da2a57ba5
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 16a0271d4cddfea6cf46d8d4f4d2af59479c4d2d
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2018
ms.locfileid: "35407937"
---
# <a name="extract-data-by-using-the-odbc-source"></a>Extraer datos mediante el origen de ODBC
  Este procedimiento describe cómo extraer datos mediante un origen ODBC. Para agregar y configurar un origen ODBC, el paquete ya debe incluir por lo menos una tarea Flujo de datos.  
  
### <a name="to-extract-data-using-an-odbc-source"></a>Para extraer datos mediante un origen ODBC  
  
1.  En [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], abra el paquete de [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] que desee.  
  
2.  Haga clic en la pestaña **Flujo de datos** y, a continuación, desde el **cuadro de herramientas**, arrastre el origen ODBC a la superficie de diseño.  
  
3.  Haga doble clic en el origen ODBC.  
  
4.  En el cuadro de diálogo **Editor de origen ODBC** , en la página **Administrador de conexiones** , seleccione un administrador de conexiones ODBC o haga clic en **Nuevo** para crear un nuevo administrador de conexiones.  
  
5.  Seleccione el método de acceso de datos.  
  
    -   **Nombre de la tabla**: seleccione una tabla o vista en la base de datos o escriba una expresión regular para identificar la tabla con la que el administrador de conexiones ODBC se conecta.  
  
         Esta lista contiene solo las 1000 primeras tablas. Si la base de datos contiene más de 1000 tablas, puede escribir el principio de un nombre de tabla o usar el comodín (*) para escribir cualquier parte del nombre con el fin de mostrar la tabla o las tablas que desea usar.  
  
    -   **Comando SQL**: escriba un comando SQL o haga clic en **Examinar** para cargar la consulta SQL desde un archivo de texto.  
  
6.  Puede hacer clic en **Vista previa** para ver hasta 200 filas de los datos extraídos por el origen ODBC.  
  
7.  Para actualizar la asignación entre las columnas externas y de salida, haga clic en **Columnas** y seleccione diferentes columnas en la lista **Columna externa** .  
  
8.  Si es necesario actualice los nombres de las columnas de salida modificando los valores en la lista **Columna de salida** .  
  
9. Para configurar la salida de error, haga clic en **Salida de error**.  
  
10. Haga clic en **Aceptar**.  
  
11. Para guardar el paquete actualizado, haga clic en **Guardar los elementos seleccionados**, en el menú **Archivo**.  
  
## <a name="see-also"></a>Ver también  
 [Editor de orígenes ODBC &#40;página Administrador de conexiones&#41;](../../integration-services/data-flow/odbc-source-editor-connection-manager-page.md)   
 [Editor de orígenes ODBC &#40;página Columnas&#41;](../../integration-services/data-flow/odbc-source-editor-columns-page.md)   
 [Editor de orígenes ODBC &#40;página Salida de error&#41;](../../integration-services/data-flow/odbc-source-editor-error-output-page.md)  
  
  
