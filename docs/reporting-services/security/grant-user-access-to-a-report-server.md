---
title: Conceder a un usuario acceso a un servidor de informes | Microsoft Docs
ms.custom: ''
ms.date: 05/15/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: security
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- permissions [Reporting Services], granting report server access
- roles [Reporting Services], assignments
- modifying role assignments
- deleting role assignments
ms.assetid: 2144c020-3253-4b47-8cda-e14c928bb471
caps.latest.revision: 54
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: e4b791188a0af8143ed25841906f7192f0417546
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38038433"
---
# <a name="grant-user-access-to-a-report-server"></a>Conceder a un usuario acceso a un servidor de informes

[!INCLUDE[ssrs-appliesto-sql2016-preview](../../includes/ssrs-appliesto-sql2016-preview.md)]

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] usa la seguridad basada en roles para conceder a un usuario acceso a un servidor de informes. En una nueva instalación del servidor de informes, solo los usuarios que son miembros del grupo local de administradores tienen los permisos para acceder a las operaciones y al contenido del servidor de informes. Para hacer que el servidor de informes esté disponible para otros usuarios, debe crear asignaciones de roles que asignen cuentas de usuario o de grupo a un rol predefinido que especifique una recopilación de tareas.

 **Servidores de informes en modo de SharePoint** : para un servidor de informes que está configurado para el modo integrado de SharePoint, el acceso se configura desde un sitio de SharePoint mediante los permisos de SharePoint. Los niveles de permisos del sitio de SharePoint determinan el acceso a las operaciones y el contenido del servidor de informes. Debe ser un administrador de sitio para conceder permisos en un sitio de SharePoint. Para obtener más información, vea [Conceder permisos sobre elementos del servidor de informes en un sitio de SharePoint](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md).

 **Servidores de informes en modo nativo**: este tema se centra en un servidor de informes configurado para el modo nativo y en el uso del portal web para asignar un rol a los usuarios. Hay dos tipos de roles:

- Los roles de nivel de elemento se usan para ver, agregar y administrar el contenido del servidor de informes, las suscripciones, el procesamiento de informes y el historial de informes. Las asignaciones de roles de nivel de elemento se definen en el nodo raíz (la carpeta Inicio) o en carpetas o elementos específicos en un nivel inferior de la jerarquía.

- Los roles de nivel de sistema permiten el acceso a las operaciones de todo el sitio que no se enlazan a ningún elemento específico. Los ejemplos incluyen el uso del Generador de informes y el uso de las programaciones compartidas.

    Los dos tipos de roles se complementan entre sí y deben usarse juntos. Por esta razón, agregar un usuario a un servidor de informes es una operación con dos partes implicadas. Si asigna un usuario a un rol de nivel de elemento, también deberá asignarlo a un rol de nivel de sistema. Al asignar un usuario a un rol, debe seleccionar un rol que ya esté definido. Para crear, modificar o eliminar roles, use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Para más información, consulte [Crear, eliminar o modificar un rol &#40;Management Studio&#41;](../../reporting-services/security/role-definitions-create-delete-or-modify.md).

## <a name="before-you-start"></a>Antes de empezar

Revise la lista siguiente antes de agregar usuarios a un servidor de informes en modo nativo.

- Debe ser miembro del grupo local de administradores en el equipo del servidor de informes. Si implementa [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] o Windows Server 2008, se requiere la configuración adicional antes de poder administrar localmente un servidor de informes. Para obtener más información, vea [Configurar un servidor de informes en modo nativo para la administración local](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).

- Para delegar esta tarea en otros usuarios, cree asignaciones de roles que asignen cuentas de usuario a los roles de administrador de contenido y de sistema. Los usuarios con permisos de administrador de contenido y de sistema pueden agregar usuarios a un servidor de informes.

- En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], vea los roles predefinidos para Roles del sistema y Roles del usuario para familiarizarse con los tipos de tareas de cada rol. Las descripciones de tareas no están visibles en el portal web, de modo que se recomienda familiarizarse con los roles antes de empezar a agregar usuarios.

- Si lo desea, personalice los roles o defina roles adicionales para incluir la recopilación de tareas que necesita. Por ejemplo, si piensa usar la configuración de seguridad personalizada para los elementos individuales, quizá desee crear una nueva definición de roles que permita el acceso a la vista de carpetas.

### <a name="to-add-a-user-or-group-to-a-system-role"></a>Para agregar un usuario o un grupo al rol del sistema.

1. Inicie el [portal web](../web-portal-ssrs-native-mode.md).

2. Seleccione el *icono de engranaje* de la esquina superior derecha.

3. Seleccione **Configuración del sitio**.

4. Seleccione **Seguridad**.

5. Seleccione **Agregar grupo o usuario**.

6. En **Grupo o usuario**, especifique una cuenta de grupo o de usuario de dominio de Windows con este formato: \<dominio>\\<cuenta\>. 

    > [!NOTE]
    > Si utiliza la autenticación de formularios o la seguridad personalizada, especifique la cuenta de grupo o de usuario en el formato correcto para su implementación.

7. Seleccione un rol del sistema y luego **Aceptar**.

    Los roles son acumulativos, de modo que si selecciona Administrador del sistema y Usuario del sistema, un usuario o grupo podrá realizar las tareas en ambos roles.

8. Repita el proceso para crear asignaciones para usuarios o grupos adicionales.

### <a name="to-add-a-user-or-group-to-an-item-role"></a>Para agregar un usuario o grupo al rol del elemento

1. Inicie el **portal web** y busque el elemento de informe para el que quiere agregar un usuario o un grupo.

2. Seleccione el carácter **...** (puntos suspensivos) en un elemento.

3. En el menú desplegable, seleccione **Administrar**.

4. Seleccione **Seguridad**.

5. Seleccione **Agregar grupo o usuario**.

    > [!NOTE]
    > Si un elemento hereda la seguridad de un elemento primario, en la barra de herramientas, seleccione **Personalizar seguridad** para cambiar la configuración de seguridad. Luego seleccione **Agregar grupo o usuario**.

6. En **Grupo o usuario**, especifique una cuenta de grupo o de usuario de dominio de Windows con este formato: \<dominio>\\<cuenta\>. Si utiliza la autenticación de formularios o la seguridad personalizada, especifique la cuenta de grupo o de usuario en el formato correcto para su implementación.

7. Seleccione una o varias definiciones de roles que describan la manera en que el usuario o el grupo debe acceder al elemento y luego seleccione **Aceptar**.

8. Repita el proceso para crear asignaciones para usuarios o grupos adicionales.

## <a name="next-steps"></a>Pasos siguientes

[Crear y administrar asignaciones de roles](../../reporting-services/security/create-and-manage-role-assignments.md)   
[Nueva asignación de roles y Editar asignación de roles &#40;páginas del Administrador de informes&#41;](http://msdn.microsoft.com/library/3319ced0-4b86-42af-b18d-da41a625113c)   
[Página de propiedades de seguridad, elementos &#40;Administrador de informes&#41;](http://msdn.microsoft.com/library/351b8503-354f-4b1b-a7ac-f1245d978da0)   
[Asignaciones de roles](../../reporting-services/security/role-assignments.md)   
[Definiciones de roles](../../reporting-services/security/role-definitions.md)  

¿Tiene alguna pregunta más? [Puede plantear sus dudas en el foro de Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231).
