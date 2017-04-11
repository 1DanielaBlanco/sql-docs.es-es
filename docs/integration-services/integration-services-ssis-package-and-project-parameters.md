---
title: "Paquete de Integration Services (SSIS) y los par&#225;metros del proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.designer.parameter.f1"
  - "sql13.dts.designer.paramterwindow.f1"
ms.assetid: 9ed9ca8e-8b1e-48d9-907d-285516d6562b
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 22
---
# Paquete de Integration Services (SSIS) y los par&#225;metros del proyecto
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Parámetros (SSIS) permiten asignar valores a propiedades de los paquetes en el momento de la ejecución del paquete. Puede crear *parámetros de proyecto* en el nivel de proyecto y *parámetros de paquete* en el nivel de paquete. Los parámetros de proyecto se usan para proporcionar cualquier entrada externa que el proyecto recibe a uno o más paquetes del proyecto. Los parámetros de paquete permiten modificar la ejecución del paquete sin tener que modificarlo ni volver a implementarlo.  
  
 En [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] puede crear, modificar o eliminar parámetros del proyecto en la ventana **Project.params** . Para crear, modificar y eliminar los parámetros de paquetes, use la pestaña **Parámetros** en el Diseñador de [!INCLUDE[ssIS](../includes/ssis-md.md)] . Puede asociar un parámetro nuevo o existente a una propiedad de tarea con el cuadro de diálogo **Parametrizar** . Para obtener más información sobre cómo usar la ventana **Project.params** y las pestaña **Parámetros** , vea [Create Parameters](../Topic/Create%20Parameters.md). Para obtener más información acerca del cuadro de diálogo **Parametrizar** , vea [Parameterize Dialog Box](../Topic/Parameterize%20Dialog%20Box.md).  
  
## Parámetros y modelo de implementación de paquetes  
 En general, si implementa un paquete con el modelo de implementación de paquetes, debe utilizar configuraciones en lugar de parámetros.  
  
 Al implementar un paquete que contenga parámetros utilizando el modelo de implementación de paquetes y después ejecutar el paquete, los parámetros no se llaman durante la ejecución. Si el paquete contiene parámetros de paquetes y las expresiones dentro del paquete utilizan los parámetros, los valores resultantes se aplican en tiempo de ejecución. Si el paquete contiene parámetros de proyecto, la ejecución del paquete puede producir un error.  
  
## Modelo de implementación de proyectos y paquetes  
 Al implementar un proyecto en el servidor de Integration Services (SSIS), use las vistas, procedimientos almacenados y el [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Administrar parámetros del proyecto y el paquete de interfaz de usuario. Para obtener más información, vea los siguientes temas.  
  
-   [Vistas & #40; catálogo de Integration Services & #41;](../integration-services/system-views/views-integration-services-catalog.md)  
  
-   [Almacenado procedimientos & #40; catálogo de Integration Services & #41;](../integration-services/system-stored-procedures/stored-procedures-integration-services-catalog.md)  
  
-   [Cuadro de diálogo Configurar](../integration-services/service/configure-dialog-box.md)  
  
-   [Cuadro de diálogo Ejecutar paquete](../integration-services/packages/execute-package-dialog-box.md)  
  
### Valores de parámetros  
 Puede asignar hasta tres tipos de valores para un parámetro. Cuando se inicia la ejecución del paquete, se utiliza un único valor para el parámetro y el parámetro se resuelve en un valor literal final.  
  
 La tabla siguiente enumera los tipos de valores.  
  
|Nombre del valor|Descripción|Tipo del valor|  
|----------------|-----------------|-------------------|  
|Valor de ejecución|El valor asignado a una instancia específica de la ejecución del paquete. Esta asignación invalida todos los demás valores, pero solo se aplica a una única instancia de ejecución del paquete.|Literal|  
|Valor de servidor|El valor asignado al parámetro dentro del ámbito del proyecto, una vez que el proyecto se implementa en el servidor de Integration Services. Este valor invalida el valor predeterminado de diseño.|Literal o referencia de variable de entorno|  
|Valor de diseño|El valor asignado al parámetro cuando el proyecto se crea o modifica en [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Este valor se mantiene con el proyecto.|Literal|  
  
 Puede utilizar un único parámetro para asignar un valor a varias propiedades del paquete. A una propiedad del paquete se le puede asignar un valor solo de un único parámetro.  
  
###  <a name="executions"></a> Ejecuciones y valores de parámetros  
 La *ejecución* es un objeto que representa una sola instancia de ejecución del paquete. Cuando se crea una ejecución, debe especificar todos los detalles para ejecutar un paquete como los valores de los parámetros de ejecución. También puede modificar los valores de parámetros para las ejecuciones existentes.  
  
 Cuando se establece explícitamente un valor de parámetro de ejecución, el valor solo es aplicable a esa instancia de ejecución concreta. El valor de ejecución se utiliza en lugar de un valor de servidor o de un valor de diseño. Si no establece explícitamente un valor de ejecución y se ha especificado un valor de servidor, se utiliza el valor del servidor.  
  
 Si un parámetro se marca como sea necesario, se debe especificar el valor de servidor o el valor de ejecución para ese parámetro. De lo contrario, el paquete correspondiente no se ejecuta. Aunque el parámetro tenga un valor predeterminado en tiempo de diseño, nunca se usará una vez que se implemente el proyecto.  
  
#### Variables de entorno  
 Si un parámetro hace referencia a una variable de entorno, el valor literal de esa variable se resuelve mediante la referencia de entorno especificada y se aplica al parámetro. El valor del parámetro literal final que se utiliza para la ejecución del paquete se conoce como valor de parámetro de ejecución. Especifica la referencia de entorno para una ejecución mediante el cuadro de diálogo **Ejecutar**  
  
 Si un parámetro de proyecto hace referencia a una variable de entorno y el valor literal de la variable no puede resolverse en la ejecución, se utiliza el valor de diseño. El valor del servidor no se utiliza.  
  
 Para ver las variables de entorno que se asignan a los valores de parámetro, consulte la vista catalog.object_parameters. Para obtener más información, consulte [catalog.object_parameters & #40; SSISDB #41; & base de datos](../integration-services/system-views/catalog-object-parameters-ssisdb-database.md).  
  
#### Determinar los valores de parámetros de ejecución  
 Pueden utilizarse las vistas y el procedimiento almacenado siguientes de Transact-SQL para mostrar y establecer los valores de parámetro.  
  
 [Catalog.execution_parameter_values & #40; SSISDB #41; & base de datos](../integration-services/system-views/catalog-execution-parameter-values-ssisdb-database.md)(vista)  
 Muestra los valores de parámetros reales que serán utilizados por una ejecución concreta  
  
 [Catalog.get_parameter_values & #40; SSISDB #41; & base de datos](../integration-services/system-stored-procedures/catalog-get-parameter-values-ssisdb-database.md) (procedimiento almacenado)  
 Resuelve y muestra los valores reales del paquete y la referencia de entorno especificados  
  
 [Catalog.object_parameters & #40; SSISDB #41; & base de datos](../integration-services/system-views/catalog-object-parameters-ssisdb-database.md) (vista)  
 Muestra los parámetros y las propiedades de todos los paquetes y proyectos en el catálogo de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , incluidos los valores predeterminados de servidor y de diseño.  
  
 [Catalog.set_execution_parameter_value & #40; Base de datos SSISDB & #41;](../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)  
 Establece el valor de un parámetro para una instancia de ejecución en el catálogo [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 También puede utilizar el cuadro de diálogo **Ejecutar paquete** en [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] para modificar el valor de parámetro. Para obtener más información, vea [Execute Package Dialog Box](../integration-services/packages/execute-package-dialog-box.md).  
  
 También puede utilizar el dtexec **/parámetro** opción para modificar un valor de parámetro. Para más información, consulte [dtexec Utility](../integration-services/packages/dtexec-utility.md).  
  
### Validación de parámetros  
 Si los valores de parámetros no se pueden resolver, la ejecución del paquete correspondiente generará un error. Para ayudar a evitar errores, puede validar los proyectos y los paquetes mediante el cuadro de diálogo **Validar** en [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. La validación permite confirmar que todos los parámetros tienen los valores necesarios o pueden resolver los valores necesarios con referencias de entorno específicas. La validación comprueba también otros problemas comunes del paquete.  
  
 Para obtener más información, vea [Validate Dialog Box](../integration-services/service/validate-dialog-box.md).  
  
### Ejemplo de parámetro  
 En este ejemplo se describe un parámetro denominado **pkgOptions** que se utiliza para especificar opciones para el paquete en que reside.  
  
 En tiempo de diseño, cuando el parámetro se creó en [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], se asignó al parámetro el valor predeterminado 1. Este valor predeterminado se conoce como valor predeterminado de diseño. Si el proyecto se implementó en el catálogo de SSISDB y no se asignaron otros valores a este parámetro, se asignará a la propiedad del paquete correspondiente al parámetro **pkgOptions** el valor 1 durante la ejecución del paquete. El valor predeterminado de diseño se mantiene con el proyecto en su ciclo de vida.  
  
 En la preparación de una instancia específica de la ejecución del paquete, se asigna el valor 5 al parámetro **pkgOptions** . Este valor se conoce como valor de ejecución porque se aplica al parámetro solo para esa instancia concreta de ejecución. Cuando se inicia la ejecución, se asigna el valor 5 a la propiedad del paquete correspondiente al parámetro **pkgOptions** .  
  
## Tareas relacionadas  
 [Crear parámetros](../Topic/Create%20Parameters.md)  
  
 [Establecer valores de parámetro después de la implementación del proyecto](../Topic/Set%20Parameter%20Values%20After%20the%20Project%20Is%20Deployed.md)  
  
## Contenido relacionado  
 Entrada de blog, [Sugerencia rápida de SSIS: parámetros necesarios](http://go.microsoft.com/fwlink/?LinkId=239781), en mattmasson.com.  
  
  