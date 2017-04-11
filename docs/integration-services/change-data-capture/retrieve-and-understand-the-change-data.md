---
title: "Recuperar y describir datos modificados | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "carga incremental [Integration Services], recuperar datos"
ms.assetid: af366697-6942-42bb-aea5-18fdef018965
caps.latest.revision: 30
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 30
---
# Recuperar y describir datos modificados
  En el flujo de datos de un paquete de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] que realiza una carga incremental de datos modificados, la primera tarea consiste en ejecutar la consulta que recupera los datos modificados. Esta consulta se ejecuta dentro de un componente de origen en una tarea Flujo de Datos. A continuación, pueden utilizarse transformaciones y destinos de nivel inferior para aplicar los datos modificados a un destino.  
  
> [!NOTE]  
>  La creación de una consulta que contiene una función con valores de tabla es el tercer paso en el proceso de crear un paquete que realiza una carga incremental de datos modificados. Para obtener más información sobre esta consulta, vea [Crear la función para recuperar los datos modificados](../../integration-services/change-data-capture/create-the-function-to-retrieve-the-change-data.md). Para obtener una descripción del proceso general de creación de un paquete que realiza una carga incremental de los datos modificados, vea [Captura de datos modificados &#40;SSIS&#41;](../../integration-services/change-data-capture/change-data-capture-ssis.md).  
  
## Agregar la tarea Flujo de datos  
 En el flujo de datos del paquete, se recuperan los datos modificados, se separan las filas basándose en el tipo de cambio que se produjo y, a continuación, se aplican los cambios al destino.  
  
#### Para agregar una tarea Flujo de datos al paquete  
  
1.  En la pestaña [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]Flujo de control **de** , agregue una tarea Flujo de datos.  
  
2.  Conecte la tarea anterior que preparó la cadena de consulta con la tarea Flujo de datos.  
  
## Configurar el componente de origen para consultar los cambios  
 El componente de origen utiliza la cadena de consulta que se preparó y se almacenó en una variable para llamar a la función con valores de tabla que recupera los datos que han cambiado.  
  
> [!NOTE]  
>  Para obtener más información sobre la cadena de consulta que se preparó y se almacenó en una variable, vea [Preparar para consultar datos modificados](../../integration-services/change-data-capture/prepare-to-query-for-the-change-data.md). Para obtener más información sobre la función con valores de tabla que recupera los datos modificados, vea [Crear la función para recuperar los datos modificados](../../integration-services/change-data-capture/create-the-function-to-retrieve-the-change-data.md).  
  
#### Para configurar un origen de OLE DB para recuperar los datos modificados  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], en la pestaña **Flujo de datos** , agregue un origen de OLE DB.  
  
2.  En el **Editor de origen de OLE DB**, en la página **Administrador de conexiones** , seleccione las opciones siguientes:  
  
    1.  Configure una conexión válida con una base de datos de origen.  
  
    2.  Para **Modo de acceso a datos**, seleccione **Comando SQL de variable**.  
  
    3.  Para **Nombre de variable**, seleccione **User::SqlDataQuery**.  
  
3.  En el **Editor de origen de OLE DB**, en la página **Columnas** , asegúrese de que todas las columnas que desea están asignadas a columnas de resultados.  
  
## Paso siguiente  
 Después de haber configurado un origen de OLE DB para recuperar los datos modificados, el paso siguiente consiste en iniciar el diseño del flujo de datos del paquete.  
  
 **Tema siguiente:** [Procesar inserciones, actualizaciones y eliminaciones](../../integration-services/change-data-capture/process-inserts-updates-and-deletes.md).  
  
  