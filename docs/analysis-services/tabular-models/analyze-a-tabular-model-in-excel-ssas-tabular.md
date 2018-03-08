---
title: Analizar un modelo tabular en Excel | Documentos de Microsoft
ms.custom: 
ms.date: 02/21/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.bidtoolset.chooseperspect.f1
ms.assetid: 47fa45fc-60ab-41a1-bde3-5781c8462889
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6b9248c15ba18811781fe24ae3f432e61b7df540
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="analyze-a-tabular-model-in-excel"></a>Analizar un modelo tabular en Excel  
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
La característica Analizar en Excel de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] abre Microsoft Excel, crea una conexión de origen de datos con la base de datos del área de trabajo del modelo y agrega una tabla dinámica a la hoja de cálculo. Los objetos del modelo (tablas, columnas, medidas, jerarquías y KPI) se incluyen como campos en la lista de campos de la tabla dinámica.  
  
> [!NOTE]  
>  Para usar la característica Analizar en Excel, tiene que tener instalado Microsoft Office 2003 o posterior en el mismo equipo que [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Si Office no está instalado en el mismo equipo, puede usar Excel en otro equipo y conectarse a la base de datos del área de trabajo del modelo como un origen de datos. A continuación, podrá agregar manualmente una tabla dinámica a la hoja de cálculo. Los objetos del modelo (tablas, columnas, medidas y KPI) se incluyen como campos en la lista de campos de la tabla dinámica.  
  
## <a name="tasks"></a>Tareas  
  
#### <a name="to-analyze-a-tabular-model-project-by-using-the-analyze-in-excel-feature"></a>Para analizar un proyecto de modelo tabular mediante la característica Analizar en Excel  
  
1.  En [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], haga clic en el menú **Modelo** y después en **Analizar en Excel**.  
  
2.  En el cuadro de diálogo **Elegir credenciales y perspectivas** , seleccione una de las opciones de credenciales siguientes para conectarse al origen de datos del área de trabajo del modelo:  
  
    -   Para usar la cuenta de usuario actual, seleccione **Usuario de Windows actual**.  
  
    -   Para usar una cuenta de usuario diferente, seleccione **Otro usuario de Windows**.  
  
         Normalmente, esta cuenta de usuario será un miembro de un rol. No se requiere una contraseña. La cuenta solo se puede utilizar en el contexto de una conexión de Excel a la base de datos del área de trabajo.  
  
    -   Para usar un rol de seguridad, seleccione **Rol**y, a continuación, en el cuadro de lista, seleccione uno o varios roles.  
  
         Los roles de seguridad se deben definir mediante el Administrador de roles. Para obtener más información, consulte [crear y administrar funciones](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md).  
  
3.  Para usar una perspectiva, seleccione una en el cuadro de lista **Perspectiva** .  
  
     Las perspectivas (distintas de las predeterminadas) se deben definir mediante el cuadro de diálogo Perspectivas. Para obtener más información, consulte [crear y administrar perspectivas](../../analysis-services/tabular-models/create-and-manage-perspectives-ssas-tabular.md).  
  
> [!NOTE]  
>  La lista de campos de tabla dinámica de Excel no se actualiza automáticamente a medida que se realizan cambios en el proyecto de modelos en el diseñador de modelos. Para actualizar dicha lista, en Excel, haga clic en **Actualizar** en la cinta **Opciones**.  
  
## <a name="see-also"></a>Vea también  
 [Analizar en Excel](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)  
  
  
