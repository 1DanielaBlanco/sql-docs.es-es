---
title: "Crear InfoCube para datos de transacción | Documentos de Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 673cea01-a260-4fce-a1a0-f73839289805
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3abae6f0ecf09b1b0156bedfb584570ed7bb45cd
ms.contentlocale: es-es
ms.lasthandoff: 08/03/2017

---
# <a name="create-infocube-for-transaction-data"></a>Crear InfoCube para los datos de transacción
  Use el cuadro de diálogo **Crear InfoCube para los datos de transacción** para crear un InfoCube nuevo para los datos de transacciones en el sistema SAP Netweaver BW.  
  
 Puede abrir el cuadro de diálogo **Crear InfoCube para los datos de transacción** desde la página **Administrador de conexiones** del **Editor de destino de SAP BW**. Para obtener más información acerca del destino de SAP BW, vea [SAP BW Destination](../../integration-services/data-flow/sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  La documentación de Microsoft Connector 1.1 for SAP BW da por supuesto que se está familiarizado con el entorno SAP Netweaver BW. Para obtener más información acerca de SAP Netweaver BW, o sobre cómo configurar los objetos y los procesos de SAP Netweaver BW, vea la documentación de SAP.  
  
 **Para abrir el cuadro de diálogo Crear InfoCube para los datos de transacción**  
  
1.  En [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], abra el paquete de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] que contiene el destino SAP BW.  
  
2.  En la pestaña **Flujo de datos** , haga doble clic en el destino de SAP BW.  
  
3.  En **Editor de destino SAP BW**, haga clic en **Administrador de conexiones** para abrir la página **Administrador de conexiones** del editor.  
  
4.  En la página **Administrador de conexiones** , en el cuadro del grupo **Crear objetos de SAP BW** , seleccione **InfoCube**y, a continuación, haga clic en **Crear**.  
  
## <a name="general-options"></a>Opciones de General  
 **Nombre de InfoCube**  
 Permite escribir un nombre para el nuevo InfoCube.  
  
 **Descripción larga**  
 Permite escribir una descripción para el nuevo InfoCube.  
  
 **Guardar y activar**  
 Permite guardar y activar el nuevo InfoCube.  
  
## <a name="infocube-transfer-structure-options"></a>Opciones de la estructura de transferencia de InfoCube  
 La sección sobre la estructura de transferencia de InfoCube permite asociar columnas del flujo de datos a InfoObjects.  
  
 **PipelineElement**  
 Permite mostrar la columna en la salida del flujo de datos que está conectada al destino de SAP BW.  
  
 **PipelineDataType**  
 Permite mostrar el tipo de datos de la columna del flujo de datos.  
  
 **InfoObject**  
 Permite mostrar el nombre del InfoObject que está asociado a la columna del flujo datos.  
  
 **Tipo**  
 Permite mostrar el tipo del InfoObject que está asociado a la columna del flujo datos. En la siguiente tabla se muestran los posibles valores para el tipo.  
  
|Value|Description|  
|-----------|-----------------|  
|CHA|Características|  
|UNI|Unidades|  
|KYF|Cifras clave|  
|TIM|Características de tiempo|  
  
 **IObject - Buscar**  
 Permite asociar un InfoObject existente a la columna de flujo de datos de la fila actual. Para efectuar este tipo de asociación, haga clic en **Buscar**y, a continuación use el cuadro de diálogo **Buscar InfoObject** para seleccionar el InfoObject existente. Para obtener más información sobre este cuadro de diálogo, vea [Look Up InfoObject](../../integration-services/data-flow/look-up-infoobject.md).  
  
 Después de seleccionar un InfoObject existente, el componente rellena las columnas **InfoObject** y **Tipo** con los valores seleccionados.  
  
 **IObject - Nuevo**  
 Permite crear un InfoObject nuevo y asociarlo a la columna de flujo de datos de la fila actual. Para crear el InfoObject nuevo, haga clic en **Nuevo**y, a continuación, use el cuadro de diálogo **Crear nuevo InfoObject** para crear el InfoObject. Para obtener más información sobre este cuadro de diálogo, vea [Create New InfoObject](../../integration-services/data-flow/create-new-infoobject.md).  
  
 Después haber creado un InfoObject nuevo, el componente rellena las columnas **InfoObject** y **Tipo** con los valores nuevos.  
  
 **IObject - Quitar**  
 Permite quitar la asociación entre el InfoObject y la columna de flujo de datos de la fila actual. Para quitar esta asociación, haga clic en **Quitar**.  
  
## <a name="see-also"></a>Vea también  
 [Ayuda F1 de Microsoft Connector 1.1 for SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  

