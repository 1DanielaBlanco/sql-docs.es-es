---
title: "Opciones de solicitud de perfil de proporción de columnas nulas de columna (tarea de generación de perfiles de datos) | Documentos de Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: 157ef8e4-fd23-4f81-8194-eebf74e9fd86
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f0cfbec0b81d1a80a813d8fc2c7e7212b33b77a4
ms.contentlocale: es-es
ms.lasthandoff: 08/03/2017

---
# <a name="column-null-ratio-profile-request-options-data-profiling-task"></a>Opciones de Solicitud de perfil de proporción de columnas nulas (tarea de generación de perfiles de datos)
  Utilice el panel **Propiedades de la solicitud** de la página **Solicitudes de perfil** para establecer las opciones de **Solicitud de perfil de proporción de columnas nulas** seleccionadas en el panel de solicitudes. Un perfil de proporción de columnas nulas indica el porcentaje de valores nulos de la columna seleccionada. Este perfil puede ayudarle a identificar problemas en los datos, por ejemplo una proporción inesperadamente alta de valores nulos en una columna. Por ejemplo, un perfil de proporción de columnas nulas puede generar un perfil de una columna de códigos postales y detectar que falta un porcentaje inaceptablemente alto de códigos postales.  
  
> [!NOTE]  
>  Las opciones que se describen en este tema aparecen en la página **Solicitudes de perfil** del **Editor de tareas de generación de perfiles de datos**. Para obtener más información sobre esta página del editor, vea [Editor de tareas de generación de perfiles de datos &#40;página Solicitudes de perfil&#41;](../../integration-services/control-flow/data-profiling-task-editor-profile-requests-page.md).  
  
 Para obtener más información sobre cómo usar la tarea de generación de perfiles de datos, vea [Configuración de la Tarea de generación de perfiles de datos](../../integration-services/control-flow/setup-of-the-data-profiling-task.md). Para obtener más información sobre cómo usar el Visor de perfil de datos para analizar la salida de la tarea de generación de perfiles de datos, vea [Visor de perfil de datos](../../integration-services/control-flow/data-profile-viewer.md).  
  
## <a name="request-properties-options"></a>Opciones de Propiedades de la solicitud  
 Para cada **Solicitud de perfil de proporción de columnas nulas**, el panel **Propiedades de la solicitud** muestra los grupos de opciones siguientes:  
  
-   **Data**, que incluye las opciones **TableOrView** y **Column**  
  
-   **General**  
  
### <a name="data-options"></a>Opciones de Data  
 **ConnectionManager**  
 Seleccione el administrador de conexiones de [!INCLUDE[vstecado](../../includes/vstecado-md.md)] existente que usa el proveedor de datos .NET para [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SqlClient) con el fin de conectarse a la base de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que contiene la tabla o la vista con la que se va a generar el perfil.  
  
 **TableOrView**  
 Seleccione la tabla o vista existente que contenga la columna de la que se va a generar un perfil.  
  
 Para obtener más información, vea la sección "Opciones de TableorView" en este tema.  
  
 **Column**  
 Seleccione la columna existente de la que se va a generar un perfil. Seleccione **(\*)** para generar un perfil de todas las columnas.  
  
 Para obtener más información, vea la sección "Opciones de Column" en este tema.  
  
#### <a name="tableorview-options"></a>Opciones de TableOrView  
 **Esquema**  
 Especifica el esquema al que pertenece la tabla seleccionada. Esta opción es de solo lectura.  
  
 **Table**  
 Muestra el nombre de la tabla seleccionada. Esta opción es de solo lectura.  
  
#### <a name="column-options"></a>Opciones de Column  
 **IsWildCard**  
 Especifica si se ha seleccionado el carácter comodín **(\*)**. Esta opción está establecida en **True** si ha seleccionado **(\*)** para generar un perfil de todas las columnas. Es **False** si ha seleccionado una columna individual para la que generar un perfil. Esta opción es de solo lectura.  
  
 **ColumnName**  
 Muestra el nombre de la columna seleccionada. Esta opción está en blanco si ha seleccionado **(\*)** para generar un perfil de todas las columnas. Esta opción es de solo lectura.  
  
 **StringCompareOptions**  
 Esta opción no se aplica al Perfil de proporción de columnas nulas.  
  
### <a name="general-options"></a>Opciones de General  
 **IdSolicitud**  
 Escriba un nombre descriptivo para identificar esta solicitud de perfil. Generalmente, no tiene que cambiar el valor generado automáticamente.  
  
## <a name="see-also"></a>Vea también  
 [Editor de la tarea &#40; de la generación de perfiles de datos Página general &#41;](../../integration-services/control-flow/data-profiling-task-editor-general-page.md)   
 [Formulario de perfil rápido de tabla única &#40; datos de generación de perfiles de tarea &#41;](../../integration-services/control-flow/single-table-quick-profile-form-data-profiling-task.md)  
  
  

