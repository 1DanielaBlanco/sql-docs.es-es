---
title: 'Lección 12: Creación de Roles | Microsoft Docs'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7ec7afeddeeb4aae53f1368f55e2af5ec3ffcd0e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "37985893"
---
# <a name="lesson-11-create-roles"></a>Lección 11: Creación de Roles
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

En esta lección, creará roles. Los roles proporcionan seguridad a los objetos y datos de la base de datos del modelo limitando el acceso únicamente a los usuarios de Windows que sean miembros del rol. Cada rol se define con un permiso único: Ninguno, Lectura, Lectura y proceso, Proceso o Administrador. Los roles se pueden definir durante la creación del modelo mediante el rol de administrador. Una vez implementado un modelo, los roles se pueden administrar con [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Para obtener más información, consulte [Roles](../analysis-services/tabular-models/roles-ssas-tabular.md).  
  
> [!NOTE]  
> No es necesario crear roles para completar este tutorial. De forma predeterminada, la cuenta con la que ha iniciado sesión tendrá privilegios Administrador para el modelo. Sin embargo, para permitir que a otros usuarios de su organización examinen el modelo mediante el uso de un cliente de informes, debe crear al menos un rol con la lectura de permisos y agregar esos usuarios como miembros.  
  
Creará tres roles:  
  
-   **Director de ventas** : este rol puede incluir a los usuarios de su organización para la que desea tener permiso para todos los objetos de modelo y datos de lectura.  
  
-   **Analista de ventas EE. UU.** : este rol puede incluir a los usuarios de su organización para que solo desea ser capaz de examinar los datos relacionados con las ventas en Estados Unidos. Para este rol, usará una fórmula DAX para definir un *Filtro de fila*, que restringe los miembros para que solo examinen los datos correspondientes a Estados Unidos.  
  
-   **Administrador** : este rol puede incluir los usuarios para el que quiera tener permisos de administrador, lo que permite acceso ilimitado y permisos para realizar tareas administrativas en la base de datos de modelo.  
  
Dado que las cuentas de usuario y grupo de Windows de su organización son únicas, puede agregar cuentas de su propia organización a los miembros. Sin embargo, para este tutorial, también puede dejar los miembros en blanco. Todavía podrá probar el efecto de cada rol más adelante en la lección 12: Analizar en Excel.  
  
Tiempo estimado para completar esta lección: **15 minutos**  
  
## <a name="prerequisites"></a>Requisitos previos  
Este tema es parte de un tutorial de creación de modelos tabulares, que se debe completar en orden. Antes de realizar las tareas en esta lección, debe haber completado la lección anterior: [lección 10: crear particiones](../analysis-services/lesson-10-create-partitions.md).  
  
## <a name="create-roles"></a>Crear roles  
  
#### <a name="to-create-a-sales-manager-user-role"></a>Para crear un rol de usuario Administrador de ventas  
  
1.  En el Explorador de modelos tabulares, haga clic en **Roles** > **Roles**.  
  
2.  En el Administrador de roles, haga clic en **New**.  
  
3.  Haga clic en el nuevo rol y, a continuación, en el **nombre** columna, cambiar el nombre del rol a **jefe de ventas**.  
  
4.  En la columna **Permisos** , haga clic en la lista desplegable y, después, seleccione el permiso **Lectura** . 

    ![como-tabular-lesson11-nueva-role](../analysis-services/media/as-tabular-lesson11-new-role.png) 
  
5.  Opcional: Haga clic en el **miembros** pestaña y, a continuación, haga clic en **agregar**. En el cuadro de diálogo **Seleccionar usuario o grupo** , especifique los usuarios o grupos de Windows de su organización que quiera incluir en el rol.  
  
#### <a name="to-create-a-sales-analyst-us-user-role"></a>Para crear un rol de usuario Analista de ventas EE. UU.  
  
1.  En el Administrador de roles, haga clic en **New**.    
  
2.  Cambiar el nombre de la función para **analista de ventas EE. UU.**  
  
3.  Asigne a este rol **lectura** permiso.  
  
4.  Haga clic en la pestaña Filtros de fila y, a continuación, para la **DimGeography** tabla solo, en la columna filtro DAX, escriba la siguiente fórmula:  
  
    ```
    =DimGeography[CountryRegionCode] = "US" 
    ```
    
    Una fórmula de filtro de fila se debe resolver como un valor booleano (TRUE o FALSE). Con esta fórmula, está especificando que solo las filas con el valor de código de país o región de "US" estarán visibles para el usuario.  
    ![como-tabular-lesson11-rol-filter](../analysis-services/media/as-tabular-lesson11-role-filter.png) 
  
6.  Opcional: Haga clic en la pestaña **Miembros** y, después, en **Agregar**. En el cuadro de diálogo **Seleccionar usuario o grupo** , especifique los usuarios o grupos de Windows de su organización que quiera incluir en el rol.  
  
#### <a name="to-create-an-administrator-user-role"></a>Para crear un rol de usuario de administrador  
  
1.  Haga clic en **Nueva**.  
  
2.  Cambiar el nombre del rol a **administrador**.  
  
3.  Asigne a este rol **administrador** permiso.  
  
4.  Opcional: Haga clic en la pestaña **Miembros** y, después, en **Agregar**. En el cuadro de diálogo **Seleccionar usuario o grupo** , especifique los usuarios o grupos de Windows de su organización que quiera incluir en el rol. 
  
  
## <a name="whats-next"></a>¿Qué sigue?
Vaya a la siguiente lección: [lección 12: analizar en Excel](../analysis-services/lesson-12-analyze-in-excel.md).

  
  
