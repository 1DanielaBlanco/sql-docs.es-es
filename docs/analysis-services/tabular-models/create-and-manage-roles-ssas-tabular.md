---
title: Crear y administrar Roles (SSAS Tabular) | Documentos de Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.bidtoolset.rolemanager.f1
- sql13.asvs.bidtoolset.roledb.f1
ms.assetid: e23d27a8-e968-4082-9dbe-963fc724b5d9
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5c625fce817af3072e059d5d2b1172383fcdafea
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="create-and-manage-roles-ssas-tabular"></a>Crear y administrar roles (SSAS tabular)
  Los roles, en los modelos tabulares, definen los permisos de los miembros para un modelo. Los roles se definen para un proyecto de modelos mediante el cuadro de diálogo Administrador de roles de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Al implementar un modelo, los administradores de bases de datos pueden administrar los roles mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Las tareas de este tema explican cómo crear y administrar roles durante la creación de modelos mediante el cuadro de diálogo Administrador de roles en [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Para obtener información sobre cómo administrar roles en una base de datos modelo implementada, vea [Roles de modelos tabulares &#40;SSAS tabular&#41;](../../analysis-services/tabular-models/tabular-model-roles-ssas-tabular.md).  
  
## <a name="tasks"></a>Tareas  
 Para crear, modificar, copiar y eliminar roles, utilice el cuadro de diálogo **Administrador de roles** . Para ver el cuadro de diálogo **Administrador de roles** , en [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], haga clic en el menú **Modelo** y en **Administrador de roles**.  
  
###  <a name="bkmk_new_role"></a> Para crear un rol  
  
1.  En [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], haga clic en el menú **Modelo** y en **Administrador de roles**.  
  
2.  En el cuadro de diálogo **Administrador de roles** , haga clic en **Nuevo**.  
  
     Se agregará un nuevo rol resaltado a la lista de roles.  
  
3.  En la lista **Roles** , en el campo **Nombre** , escriba un nombre para el rol.  
  
     De forma predeterminada, el nombre del rol predeterminado se incrementará numéricamente para cada nuevo rol. Se recomienda escribir un nombre que identifique claramente el tipo de miembro, por ejemplo, Administradores financieros o Especialistas en recursos humanos.  
  
4.  En el campo **Permisos** , haga clic en la flecha abajo y seleccione uno de los tipos de permisos siguientes:  
  
    |Permiso|Description|  
    |----------------|-----------------|  
    |**None**|Los miembros no pueden realizar ninguna modificación en el esquema del modelo y no pueden consultar los datos.|  
    |**Lectura**|Los miembros pueden consultar los datos (según los filtros de fila), pero no pueden realizar cambios en el esquema del modelo.|  
    |**Leer y actualizar**|Los miembros pueden actualizar los datos (según los filtros de fila) y ejecutar las operaciones Procesar y Procesar todo, pero no pueden realizar cambios en el esquema del modelo.|  
    |**Procesar**|Los miembros pueden ejecutar las operaciones Procesar y Procesar todo. No pueden modificar el esquema del modelo y no pueden consultar los datos.|  
    |**Administrador**|Los miembros pueden realizar modificaciones en el esquema del modelo y pueden consultar todos los datos.|  
  
5.  Para especificar una descripción para el rol, haga clic en el campo **Descripción** y escriba una descripción.  
  
6.  Si el rol que está creando tiene permiso de lectura o de lectura y procesamiento, puede agregar filtros de fila mediante una fórmula de DAX. Para agregar filtros de fila, haga clic en la pestaña **Filtros de fila** , seleccione una tabla, haga clic en el campo **Filtro DAX** y, a continuación, escriba una fórmula de DAX.  
  
7.  Para agregar miembros al rol, haga clic en la pestaña **Miembros** y, a continuación, haga clic en **Agregar**.  
  
    > [!NOTE]  
    >  También se pueden agregar miembros de rol a un modelo implementado mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Para más información, vea [Administrar roles usando SSMS &#40;SSAS tabular&#41;](../../analysis-services/tabular-models/manage-roles-by-using-ssms-ssas-tabular.md).  
  
8.  En el cuadro de diálogo **Seleccionar usuarios o grupos** , especifique el usuario de Windows o los objetos de grupo de Windows como miembros.  
  
9. Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Roles &#40;SSAS tabular&#41;](../../analysis-services/tabular-models/roles-ssas-tabular.md)   
 [Perspectivas &#40;SSAS tabular&#41;](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Analizar en Excel &#40; SSAS Tabular &#41;](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)   
 [Función USERNAME (DAX)](http://msdn.microsoft.com/en-us/22dddc4b-1648-4c89-8c93-f1151162b93f)   
 [Función CUSTOMDATA (DAX)](http://msdn.microsoft.com/en-us/58235ad8-226c-43cc-8a69-5a52ac19dd4e)  
  
  

