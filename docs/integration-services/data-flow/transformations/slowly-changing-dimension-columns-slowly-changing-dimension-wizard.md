---
title: "Columnas de dimensi&#243;n variable lenta (Asistente para dimensiones variables) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.loaddimwizard.scdsupport.f1"
ms.assetid: 36de99d5-5368-48e0-b876-17e9c6862c6c
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 23
---
# Columnas de dimensi&#243;n variable lenta (Asistente para dimensiones variables)
  Utilice el cuadro de diálogo **Columnas de dimensión variable** para seleccionar un tipo de cambio para cada una de las columnas de dimensión variable lenta.  
  
 Para obtener más información acerca de este asistente, vea [Slowly Changing Dimension Transformation](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md).  
  
## Opciones  
 **Columnas de dimensión**  
 Seleccione una columna de dimensión de la lista.  
  
 **Tipo de cambio**  
 Seleccione un **Atributo fijo** o seleccione uno de los dos tipos de atributos variables. Utilice **Atributo fijo** cuando el valor de una columna no tenga que cambiar; [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] tratará entonces los cambios como errores. Utilice **Atributo variable** para sobrescribir los valores existentes con los valores modificados. Utilice **Atributo histórico** para guardar los valores modificados en nuevos registros, al tiempo que los registros anteriores quedan marcados como desusados.  
  
 **Quitar**  
 Seleccione una columna de dimensión y quítela de la lista de columnas asignadas haciendo clic en **Quitar**.  
  
## Vea también  
 [Configurar salidas mediante el Asistente para dimensión de variación lenta](../../../integration-services/data-flow/transformations/configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  