---
title: "Seleccionar una tabla de dimensiones y claves (Asistente para dimensión de variación lenta) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.dts.loaddimwizard.selecttableandkeys.f1
ms.assetid: 01e0495f-de35-4607-ba19-0539e801e8fd
caps.latest.revision: "27"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b1806a2951e8d2cb41a44a428fe182d14c5999f0
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2017
---
# <a name="select-a-dimension-table-and-keys-slowly-changing-dimension-wizard"></a>Seleccionar una tabla de dimensiones y claves (Asistente para dimensión de variación lenta)
  Utilice la página **Seleccionar una tabla de dimensiones y claves** para seleccionar una tabla de dimensiones para cargar. Asigne columnas del flujo de datos a las columnas que se van a cargar.  
  
 Para obtener más información acerca de este asistente, vea [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Opciones  
 **Administrador de conexiones**  
 Seleccione un administrador de conexiones OLE DB existente de la lista o haga clic en **Nuevo** para crear uno nuevo.  
  
> [!NOTE]  
>  El Asistente para dimensiones de variación lenta solamente admite los administradores de conexiones OLE DB y las conexiones a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **Nuevo**  
 Use el cuadro de diálogo **Configurar el administrador de conexiones OLE DB** para seleccionar un administrador de conexiones existente o haga clic en **Nuevo** para crear una nueva conexión OLE DB.  
  
 **Tabla o vista**  
 Seleccione una tabla o una vista de la lista.  
  
 **Columnas de entrada**  
 Seleccione las columnas de la lista de columnas de entrada para las que desea especificar asignaciones.  
  
 **Columnas de dimensión**  
 Muestra todas las columnas de dimensión disponibles.  
  
 **Tipo de clave**  
 Seleccione una de las columnas de dimensión para que sea la clave empresarial. Es necesario disponer de una clave empresarial.  
  
## <a name="see-also"></a>Vea también  
 [Configurar salidas mediante el Asistente para dimensión de variación lenta](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
