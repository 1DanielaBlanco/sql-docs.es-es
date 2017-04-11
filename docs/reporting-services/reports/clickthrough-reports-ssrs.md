---
title: "Informes click-through (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "informes click-through"
  - "personalizar informes click-through"
  - "informes click-through, personalizar"
ms.assetid: cf2c396e-b0c6-41f9-8c45-ddc8406f7e85
caps.latest.revision: 28
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 28
---
# Informes click-through (SSRS)
  Un informe click-through es aquel que proporciona información detallada sobre los datos incluidos en el informe principal. Un informe click-through se muestra cuando el usuario hace clic en los datos interactivos que aparecen en el informe principal. Estos informes son generados automáticamente por el servidor de informes. El usuario, como diseñador del modelo, determina lo que se ve en los informes click-through estableciendo las propiedades **DefaultDetailAttribute** y **DefaultAggregateAttribute** que se asignan a una entidad del modelo de informe.  
  
> [!NOTE]  
>  Los informes click-through no están disponibles en todas las ediciones de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Para obtener una lista de las características admitidas por las ediciones de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vea [Características compatibles con las ediciones de SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md). Si no está seguro de la edición de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con la que trabaja su organización, póngase en contacto con el administrador de la base de datos.  
  
## Usar plantillas predeterminadas  
 De manera predeterminada, el servidor de informes genera dos tipos de plantilla click-through para cada entidad: una plantilla de una sola instancia y una plantilla de varias instancias. El elemento sobre el que haga clic determinará la plantilla que se utilizará. Si la persona que lee el informe hace clic en un atributo escalar, se utilizará la plantilla de una sola instancia. Si la persona que lee el informe hace clic en un atributo de agregado, se utilizará la plantilla de varias instancias.  
  
#### Plantillas de una sola instancia  
 Una plantilla de una sola instancia muestra todos los atributos de la entidad de destino y los atributos de agregado predeterminados que se hayan especificado para las entidades relacionadas que tienen un relación de uno a varios desde la entidad de destino. Una plantilla de una sola instancia tiene un aspecto similar al de la siguiente imagen.  
  
 ![Informe click-through varios a uno.](../../reporting-services/reports/media/manytooneclickthrough.gif "Informe click-through varios a uno.")  
  
#### Plantillas de varias instancias  
 Una plantilla de varias instancias muestra solo los atributos de detalle predeterminados de la entidad de destino y todos los atributos de agregado predeterminados que se hayan especificado para las entidades relacionadas que tienen un relación de uno a varios desde la entidad de destino. Una plantilla de varias instancias tiene un aspecto similar al de la siguiente imagen.  
  
 ![Informe click-through varios a uno.](../../reporting-services/reports/media/onetomanyclickthrough.gif "Informe click-through varios a uno.")  
  
## Personalizar informes click-through  
 En lugar de usar las plantillas predeterminadas que genera el servidor de informes, puede crear un informe en el Generador de informes y utilizarlo como informe click-through personalizado. A continuación, puede vincular el informe al modelo como un informe detallado en el Administrador de informes.  
  
 Para convertir un informe del Generador de informes en un informe click-through, debe seleccionar la opción **Permitir que los usuarios obtengan detalles de este informe a partir de otros informes** en el cuadro de diálogo **Propiedades** del Generador de informes. Una vez que esta opción se ha seleccionado, se agregará un parámetro drill-through al informe y éste ya no podrá ejecutarse directamente en el Generador de informes. El servidor de informes calcula automáticamente el parámetro drill-through cuando la persona que lee el informe hace clic en un elemento del informe del Generador de informes.  
  
> [!IMPORTANT]  
>  La entidad principal o base utilizada en el informe debe ser la misma a la que vincule el informe.  
  
## Vea también  
 [Vincular un informe a un modelo como informe click-through](../Topic/Link%20a%20Report%20to%20a%20Model%20as%20a%20Clickthrough%20Report.md)  
  
  