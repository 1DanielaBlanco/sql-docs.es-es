---
title: "Lecci&#243;n 3: Dise&#241;ar el informe primario usando el Asistente para informes | Microsoft Docs"
ms.custom: ""
ms.date: "05/18/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 2f69dcd3-cd6d-45a9-a62a-ba6f5f3179d8
caps.latest.revision: 9
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 9
---
# Lecci&#243;n 3: Dise&#241;ar el informe primario usando el Asistente para informes
Después de crear una conexión de datos y una tabla de datos para el informe primario, el paso siguiente consiste en diseñar dicho informe usando el Asistente para informes del Diseñador de informes. Para obtener más información sobre el Diseñador de informes, consulte [Diseñar informes con el Diseñador de informes &#40;SSRS&#41;](../reporting-services/tools/design-reports-with-report-designer-ssrs.md).  
  
### Para diseñar el informe primario usando el Asistente para informes  
  
1.  Asegúrese de que el sitio web de nivel superior está seleccionado en el **Explorador de soluciones**.  
  
2.  Haga clic con el botón derecho en el sitio web y seleccione **Agregar nuevo elemento**.  
  
3.  En el cuadro de diálogo **Agregar nuevo elemento**, seleccione **Asistente para informes**, escriba un nombre para el archivo de informe y, después, seleccione **Agregar**.  
  
    Así se inicia el Asistente para informes.  
  
4.  En la página **Propiedades de conjunto de datos**, en el cuadro **Origen de datos**, seleccione el **DataSet1** que creó en la [Lección 2: Definir una conexión de datos y una tabla de datos para el informe primario](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md).  
  
    El cuadro **Conjuntos de datos disponibles** se actualiza automáticamente con la **DataTable** que creó anteriormente.  
  
5.  Seleccione **Siguiente**.  
  
6.  En la página **Organizar campos**, haga lo siguiente:  
  
    1.  Arrastre **ProductID**, **Name**, **ProductNumber**, **SafetyStockLevel** y **ReorderLevel** desde **Campos disponibles** hasta el cuadro **Valores**.  
  
    2.  Seleccione la flecha situada junto a **Sum(ProductID)**, **Sum(SafetyStockLevel)** y **Sum(ReorderLevel)**, y desactive la selección de **Suma**.  
  
7.  Seleccione **Siguiente** dos veces y, después, seleccione **Finalizar** para cerrar el **Asistente para informes**.  
  
    Ahora ha creado el archivo .rdlc. El archivo se abre en el Diseñador de informes. El Tablix que se diseñó se muestra en la superficie de diseño.  
  
8.  Guarde el archivo .rdlc.  
  
## Tarea siguiente  
Ha diseñado correctamente el informe primario usando el Asistente para informes. A continuación, creará una conexión de datos y una tabla de datos para el informe secundario. Consulte la [Lección 4: Definir una conexión de datos y una tabla de datos para el informe secundario](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md).  
  
  
  
