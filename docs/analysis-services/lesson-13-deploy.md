---
title: 'Lección 14: Implementar | Documentos de Microsoft'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 533b6197c72d03876b928f4024fc5eb4fb0f2fc0
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="lesson-13-deploy"></a>Lección 13: implementar
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

En esta lección, configurará propiedades de implementación; especificar una implementación local o instancia de servidor de Azure y un nombre para el modelo. A continuación, implementará el modelo para esa instancia. Después de implementa el modelo, los usuarios pueden conectarse a él mediante el uso de una aplicación de cliente de informes. Para más información acerca de la implementación, consulte [implementación de la solución de modelo Tabular](../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md) y [implementar en Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy).  
  
Tiempo estimado para completar esta lección: **5 minutos**  
  
## <a name="prerequisites"></a>Requisitos previos  
Este tema es parte de un tutorial de creación de modelos tabulares, que se debe completar en orden. Antes de realizar las tareas en esta lección, debe haber completado la lección anterior: [lección 12: analizar en Excel](../analysis-services/lesson-12-analyze-in-excel.md).  
  
## <a name="deploy-the-model"></a>Implementar el modelo  
  
#### <a name="to-configure-deployment-properties"></a>Para configurar propiedades de implementación  
  
1.  En **el Explorador de soluciones**, haga clic en el **AW Internet Sales** del proyecto y, a continuación, haga clic en **propiedades**.  
  
2.  En el **páginas de propiedades de ventas de Internet de AW** cuadro de diálogo **el servidor de implementación**, en la **Server** propiedad, escriba el nombre de un servidor de Analysis Services de Azure o un instancia del servidor local se ejecuta en modo Tabular. Se trata el modelo se implementarán en la instancia del servidor.  

    ![AAS-implementar--server-propiedades de la implementación](../analysis-services/media/aas-deploy-deployment-server-property.png)
 
    > [!IMPORTANT]  
    > Debe tener permisos de administrador en el remoto Analysis Services instancia en orden para poder implementarlo.  
  
3.  En el **base de datos** propiedad, escriba **Adventure Works Internet Sales**.  
  
4.  En el **nombre del modelo** propiedad, escriba **Adventure Works Internet Sales Model**.  
  
5.  Compruebe las opciones seleccionadas y, después, haga clic en **Aceptar**.  
  
#### <a name="to-deploy-the-adventure-works-internet-sales-tabular-model"></a>Para implementar el modelo tabular Ventas por Internet de Adventure Works  
  
1.  En **el Explorador de soluciones**, haga clic en el **AW Internet Sales** proyecto > **generar**.  

2.  Haga clic en el **AW Internet Sales** proyecto > **implementar**.

    Cuando se implementa en Azure Analysis Services, es probable que se le pedirá que especifique su cuenta. Escriba su cuenta profesional y la contraseña, por ejemplo nancy@adventureworks.com. Esta cuenta debe ser de administradores en la instancia del servidor.
  
    Aparece el cuadro de diálogo Implementar en el que se muestra el estado de implementación de los metadatos y las tablas incluidas en el modelo.  
    
    ![estado implementar AAS](../analysis-services/media/aas-deploy-status.png)
  
3. Cuando se complete correctamente la implementación, continúe y haga clic en **Cerrar**.  
  
## <a name="conclusion"></a>Conclusión  
¡Enhorabuena! Haya terminado de crear e implementar el primer modelo Tabular de Analysis Services. Este tutorial le ha guiado por las tareas más comunes para crear un modelo tabular. Ahora que su modelo Ventas por Internet de Adventure Works está implementado, puede utilizar el SQL Server Management Studio para administrarlo, crear scripts de proceso y realizar un plan de copia de seguridad. Los usuarios ahora también pueden conectarse al modelo mediante una aplicación de cliente de informes como Microsoft Excel o Power BI.  

![como-tabular-lesson13-ssms](../analysis-services/media/as-tabular-lesson13-ssms.png)
  
  
## <a name="see-also"></a>Vea también  
[Modo DirectQuery](../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)  
[Configurar las propiedades predeterminadas de modelado de datos y de implementación](../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)  
[Bases de datos de modelo tabular](../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md)  
  
  
  ## <a name="whats-next"></a>¿Qué sigue?
*  [Lección complementaria - implemente seguridad dinámica utilizando filtros de fila](../analysis-services/supplemental-lesson-implement-dynamic-security-by-using-row-filters.md).

*  [Complementario de lecciones: configurar propiedades de informes para informes de Power View](../analysis-services/supplemental-lesson-configure-reporting-properties-for-power-view-reports.md).
