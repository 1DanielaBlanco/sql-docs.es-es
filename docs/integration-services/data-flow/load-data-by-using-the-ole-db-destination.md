---
title: Cargar datos mediante el destino de OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- loading data
- OLE DB destination [Integration Services]
- destinations [Integration Services], OLE DB
ms.assetid: 78899498-725e-4300-a7af-f983f4ea384b
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 09d7b0e3238ecdec8ef07940aa4dc5eebbf4b6c3
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2018
ms.locfileid: "35401347"
---
# <a name="load-data-by-using-the-ole-db-destination"></a>Cargar datos mediante el destino de OLE DB
  Para agregar y configurar un destino de OLE DB, el paquete ya debe incluir al menos una tarea Flujo de datos y un origen.  
  
### <a name="to-load-data-using-an-ole-db-destination"></a>Para cargar datos mediante un destino de OLE DB  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], abra el proyecto de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] que contiene el paquete que desea.  
  
2.  En el Explorador de soluciones, haga doble clic en el paquete para abrirlo.  
  
3.  Haga clic en la pestaña **Flujo de datos** y, a continuación, desde el **cuadro de herramientas**, arrastre el destino de OLE DB a la superficie de diseño.  
  
4.  Conecte el destino de OLE DB al flujo de datos arrastrando el conector desde un origen de datos o una transformación anterior al destino.  
  
5.  Haga doble clic en el destino de OLE DB.  
  
6.  En el **Editor de destino de OLE DB** , en la página **Administrador de conexiones** , seleccione un administrador de conexiones OLE DB o haga clic en **Nuevo** para crear un nuevo administrador de conexiones. Para más información, vea [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
7.  Seleccione el método de acceso de datos:  
  
    -   **Tabla o vista** Seleccione una tabla o vista en la base de datos que contiene los datos.  
  
    -   **Carga rápida de tabla o vista** Seleccione una tabla o una vista en la base de datos que contiene los datos y, después, establezca las opciones de carga rápida: **Mantener valores de identidad**, **Mantener valores NULL**, **Bloqueo de tabla**, **Restricción CHECK**, **Filas por lote**o **Tamaño máximo de confirmación de inserción**.  
  
    -   **Variable de nombre de tabla o nombre de vista** Seleccione la variable definida por el usuario que contiene el nombre de una tabla o vista en la base de datos.  
  
    -   **Carga rápida de variable de nombre de tabla o nombre de vista** Seleccione la variable definida por el usuario que contiene el nombre de una tabla o vista en la base de datos que contiene los datos y, después, establezca las opciones de carga rápida.  
  
    -   **Comando SQL** Escriba un comando SQL o haga clic en **Generar consulta** para escribir un comando SQL mediante el **Generador de consultas**.  
  
8.  Haga clic en **Asignaciones** y asigne columnas de la lista **Columnas de entrada disponibles** a columnas en la lista **Columnas de destino disponibles** arrastrando columnas de una lista a otra.  
  
    > [!NOTE]  
    >  El destino de OLE DB asigna automáticamente las columnas con el mismo nombre.  
  
9. Para configurar la salida de error, haga clic en **Salida de error**. Para más información, consulte [Debugging Data Flow](../../integration-services/troubleshooting/debugging-data-flow.md).  
  
10. Haga clic en **Aceptar**.  
  
11. Para guardar el paquete actualizado, haga clic en **Guardar los elementos seleccionados**, en el menú **Archivo**.  
  
## <a name="see-also"></a>Ver también  
 [Destino de OLE DB](../../integration-services/data-flow/ole-db-destination.md)   
 [Transformaciones de Integration Services](../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Rutas de Integration Services](../../integration-services/data-flow/integration-services-paths.md)   
 [Tarea Flujo de datos](../../integration-services/control-flow/data-flow-task.md)  
  
  
