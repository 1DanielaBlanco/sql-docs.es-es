---
title: "Lecci&#243;n 6: Uso de par&#225;metros con el modelo de implementaci&#243;n de proyectos en SSIS | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 9216f18c-1762-4f2d-8c22-bd0ab7107555
caps.latest.revision: 5
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 5
---
# Lecci&#243;n 6: Uso de par&#225;metros con el modelo de implementaci&#243;n de proyectos en SSIS
SQL Server 2012 presenta un nuevo modelo de implementación en el que puede implementar sus proyectos en el servidor de Integration Services. El servidor de Integration Services permite administrar y ejecutar paquetes, así como configurar valores en tiempo de ejecución para los paquetes.  
  
En esta lección, modificará el paquete que ha creado en la [Lección 5: Agregar configuraciones de paquete para el modelo de implementación de paquetes](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md) para usar el modelo de implementación de paquetes. Reemplazará el valor de configuración con un parámetro para especificar la ubicación de los datos de ejemplo. También puede copiar el paquete de la lección 5 completada que se incluye con el tutorial.  
  
Con el Asistente para la conversión de proyectos de Integration Services, convertirá el proyecto al modelo de implementación de proyectos y usará un parámetro en lugar de un valor de configuración para establecer la propiedad Directory. Esta lección abarca parcialmente los pasos que se seguiría para convertir paquetes SSIS existentes al nuevo modelo de implementación de proyectos.  
  
Cuando ejecute el paquete de nuevo, el servicio Integration Services usará el parámetro para rellenar el valor de la variable y la variable actualizará a su vez la propiedad Directory. Como resultado, el paquete iterará por los archivos de la nueva carpeta de datos especificada por el valor del parámetro, en lugar de iterar por la carpeta que se estableció en el archivo de configuración del paquete.  
  
> [!IMPORTANT]  
> Para este tutorial, se necesita la base de datos de ejemplo **AdventureWorksDW2012** . Para obtener más información sobre cómo instalar e implementar **AdventureWorksDW2012**, consulte [Considerations for Installing SQL Server Samples and Sample Databases](http://technet.microsoft.com/en-us/library/ms161556%28v=sql.105%29) (Consideraciones para instalar ejemplos y bases de datos de ejemplo de SQL Server).  
  
## Tareas de la lección  
Esta lección contiene las siguientes tareas:  
  
1.  [Paso 1: copiar el paquete de la lección 5](../integration-services/step-1-copying-the-lesson-5-package.md)  
  
2.  [Paso 2: Convertir el proyecto al modelo de implementación de proyectos](../integration-services/step-2-converting-the-project-to-the-project-deployment-model.md)  
  
3.  [Paso 3: Probar el paquete de la lección 6](../integration-services/step-3-testing-the-lesson-6-package.md)  
  
4.  [Paso 4: Implementar el paquete de la lección 6](../integration-services/step-4-deploying-the-lesson-6-package.md)  
  
## Iniciar la lección  
[Paso 1: copiar el paquete de la lección 5](../integration-services/step-1-copying-the-lesson-5-package.md)  
  