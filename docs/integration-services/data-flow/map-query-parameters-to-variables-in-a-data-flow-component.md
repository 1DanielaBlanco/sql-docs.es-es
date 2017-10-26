---
title: "Asignar parámetros de consulta a Variables en un componente de flujo de datos | Documentos de Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [Integration Services], parameter mapping
- parameters [Integration Services]
- mapping query parameters to variables [Integration Services]
- variables [Integration Services], mapping parameters to
ms.assetid: 5e26977c-758c-46d6-acf1-4fd9238f0950
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: da9367a56cefbb37244d4a47543b93586e7e8870
ms.contentlocale: es-es
ms.lasthandoff: 08/03/2017

---
# <a name="map-query-parameters-to-variables-in-a-data-flow-component"></a>Asignar parámetros de consulta a variables en un componente de flujo de datos
  Al configurar el origen de OLE DB para utilizar las consultas parametrizadas, puede asignar los parámetros a las variables.  
  
 El origen de OLE DB utiliza las consultas parametrizadas para filtrar los datos cuando el origen conecta con un origen de datos.  
  
### <a name="to-map-a-query-parameter-to-a-variable"></a>Para asignar un parámetro de consulta a una variable  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], abra el proyecto de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] que contiene el paquete que desea.  
  
2.  En el Explorador de soluciones, haga doble clic en el paquete para abrirlo.  
  
3.  Haga clic en la pestaña **Flujo de datos** y, a continuación, desde el **cuadro de herramientas**, arrastre el origen de OLE DB hasta la superficie de diseño.  
  
4.  Haga clic con el botón derecho en el origen de OLE DB y, después, haga clic en **Editar**.  
  
5.  En el **Editor de origen de OLE DB**, seleccione un administrador de conexiones OLE DB para conectarse al origen de datos o haga clic en **Nuevo** para crear un nuevo administrador de conexiones OLE DB.  
  
6.  Seleccione la opción **Comando SQL** para el modo de acceso a datos y, a continuación, escriba una consulta parametrizada en el panel **Texto de comando SQL** .  
  
7.  Haga clic en **Parámetros**.  
  
8.  En el **establecer parámetros de consulta** diálogo cuadro, asigne cada parámetro de la **parámetros** lista a una variable en el **Variables** lista o cree una nueva variable haciendo clic en  **\<nueva variable >**. Haga clic en **Aceptar**.  
  
    > [!NOTE]  
    >  Solo están disponibles para su asignación las variables del sistema y las variables definidas por el usuario que están en el ámbito del paquete, un contenedor principal como un bucle Foreach, o la tarea Flujo de datos que contiene el componente de flujo de datos. La variable debe tener un tipo de datos compatible con la columna en la cláusula WHERE a la que se asigna el parámetro.  
  
9. Puede hacer clic en **Vista previa** para ver hasta 200 filas de los datos que devuelve la consulta.  
  
10. Para guardar el paquete actualizado, haga clic en **Guardar los elementos seleccionados** , en el menú **Archivo** .  
  
## <a name="see-also"></a>Vea también  
 [Origen de OLE DB](../../integration-services/data-flow/ole-db-source.md)   
 [Transformación de búsqueda](../../integration-services/data-flow/transformations/lookup-transformation.md)  
  
  

