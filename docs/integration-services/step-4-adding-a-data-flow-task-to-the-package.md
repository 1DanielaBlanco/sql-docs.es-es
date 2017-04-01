---
title: "Paso 4: agregar una tarea de flujo de datos al paquete | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 96af3073-8f11-4444-b934-fe8613a2d084
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
---
# Paso 4: agregar una tarea de flujo de datos al paquete
Una vez que ha creado los administradores de conexión para los datos de origen y de destino, la siguiente tarea consiste en agregar una tarea de flujo de datos al paquete. La tarea de flujo de datos encapsula el motor de flujo de datos que mueve datos entre orígenes y destinos, y proporciona la funcionalidad para transformar, limpiar y modificar los datos a medida que se mueven. En la tarea de flujo de datos se lleva a cabo la mayor parte del proceso de extracción, transformación y carga (ETL).  
  
> [!NOTE]  
> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] separa el flujo de datos del flujo de control.  
  
### Para agregar una tarea de flujo de datos  
  
1.  Haga clic en la pestaña **Flujo de control** .  
  
2.  En el **Cuadro de herramientas de SSIS**, expanda **Favoritos** y arrastre una **tarea Flujo de datos** a la superficie de diseño de la pestaña **Flujo de control**.  
  
    > [!NOTE]  
    > Si el cuadro de herramientas de SSIS no está disponible, en el menú principal seleccione SSIS y después el cuadro de herramientas de SSIS para mostrar el cuadro de herramientas de SSIS.  
  
3.  En la superficie de diseño **Flujo de control**, haga clic con el botón derecho en la **tarea Flujo de datos** que acaba de agregar, haga clic en **Cambiar nombre** y cambie el nombre por **Extract Sample Currency Data**.  
  
    Es aconsejable proporcionar nombres únicos a todos los componentes que se agregan a una superficie de diseño. Para facilitar su uso y mantenimiento, los nombres deben describir la función que lleva a cabo cada componente. Seguir estas directrices de nomenclatura permite que los paquetes de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sean autodocumentados. Los paquetes también pueden documentarse mediante anotaciones. Para obtener más información sobre cómo usar anotaciones, consulte [Usar anotaciones en paquetes](../integration-services/use-annotations-in-packages.md).  
  
4.  Haga clic con el botón derecho en la tarea Flujo de datos, haga clic en **Propiedades** y, en la ventana Propiedades, compruebe que la propiedad **LocaleID** esté establecida en **Inglés (Estados Unidos)**.  
  
## Siguiente tarea de la lección  
[Paso 5: Agregar y configurar el origen de archivo plano](../integration-services/step-5-adding-and-configuring-the-flat-file-source.md)  
  
## Vea también  
[Tarea Flujo de datos](../integration-services/control-flow/data-flow-task.md)  
  
  
  
