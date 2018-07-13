---
title: Roles de seguridad (Analysis Services - datos multidimensionales) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], roles
- Analysis Services objects, roles
- security [Analysis Services], roles
- roles [Analysis Services], about roles
- server roles [Analysis Services]
- database roles [Analysis Services]
- roles [Analysis Services]
- storing data [Analysis Services], roles
- access rights [Analysis Services], roles
ms.assetid: 5b7e9cef-ff68-4d8e-99bc-e0094ced1baa
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 979f6302d3b03a06187d3ed1860b3c167ff66828
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37165526"
---
# <a name="security-roles--analysis-services---multidimensional-data"></a>Roles de seguridad (Analysis Services - Datos multidimensionales)
  Los roles se usan en [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] para administrar la seguridad para [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] objetos y datos. En términos simples, un rol asocia los identificadores de seguridad (SID) de usuarios de Microsoft Windows y grupos que tienen derechos de acceso específicos y los permisos definidos para los objetos administrados por una instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Se proporcionan dos tipos de roles en [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]:  
  
-   El rol del servidor, que es un rol fijo que proporciona acceso de administrador a una instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
-   Los roles de base de datos, que son roles definidos por los administradores para controlar el acceso a los objetos y datos de los usuarios que no son administradores.  
  
 Seguridad en [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] seguridad se administra mediante roles y permisos. Los roles son grupos de usuarios. Los usuarios, también denominados miembros, se pueden agregar o quitar de los roles. Los permisos de los objetos se especifican mediante los roles y todos los miembros de un rol pueden usar los objetos para los que este dispone de permiso. Todos los miembros de un rol disponen de los mismos permisos en los objetos. Los permisos son específicos de los objetos. Cada objeto cuenta con una colección de permisos que incluye los permisos concedidos en ese objeto; en un objeto se pueden conceder diferentes conjuntos de permisos. Cada permiso, de la colección de permisos del objeto, tiene un rol único asignado.  
  
## <a name="role-and-role-member-objects"></a>Objetos de rol y miembro de rol  
 Un rol es un objeto que contiene una colección de usuarios (miembros). Una definición de roles establece la pertenencia de los usuarios de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Dado que los permisos se asignan por rol, un usuario debe ser miembro de un rol para tener acceso a un objeto.  
  
 Un objeto <xref:Microsoft.AnalysisServices.Role> se compone del nombre, el identificador y los miembros de los parámetros. Los miembros son una colección de cadenas. Cada miembro contiene el nombre de usuario con el formato "dominio\nombre de usuario". El nombre es una cadena que contiene el nombre del rol. El identificador es una cadena que contiene el identificador único del rol.  
  
### <a name="server-role"></a>Rol del servidor  
 El [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] rol de servidor define el acceso administrativo de Windows usuarios y grupos a una instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Los miembros de este rol tienen acceso a todos los [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] bases de datos y objetos en una instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]y puede realizar las siguientes tareas:  
  
-   Realizar funciones administrativas de nivel de servidor con SQL Server Management Studio o [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], incluida la creación de bases de datos y el establecimiento de propiedades de nivel de servidor.  
  
-   Realizar funciones administrativas mediante programación con Objetos de administración de Análisis (AMO).  
  
-   Mantener los roles de base de datos de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
-   Iniciar seguimientos (distintas de eventos de procesamiento, que puede realizar un rol de base de datos con acceso de proceso).  
  
 Cada instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] tiene un rol de servidor que define qué usuarios pueden administrar la instancia. El nombre e Id. de este rol es Administradores y, a diferencia de los roles de base de datos, no puede eliminarse el rol del servidor ni pueden agregarse ni quitarse permisos. En otras palabras, un usuario está o no es un administrador de una instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], dependiendo de si quien está incluido en el rol de servidor para esa instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
### <a name="database-roles"></a>Roles de base de datos  
 Un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] rol de base de datos define el acceso de usuario a los objetos y datos en un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de datos. Un rol de base de datos se crea como objeto independiente en una base de datos de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] y solo se aplica a la base de datos en la que se crea el rol. El administrador incluye los usuarios y grupos de Windows en el rol y también define los permisos del rol.  
  
 Los permisos de un rol pueden permitir a los miembros obtener acceso y administrar la base de datos, además de los objetos y los datos de la misma. Cada permiso tiene uno o más derechos de acceso asociados, que a su vez proporcionan al permiso más control sobre el acceso a un objeto específico de la base de datos.  
  
## <a name="permission-objects"></a>Objetos Permission  
 Los permisos se asocian a un objeto (cubo, dimensión, otros) para un rol determinado. Los permisos especifican qué operaciones puede realizar el miembro de dicho rol en el objeto.  
  
 La clase <xref:Microsoft.AnalysisServices.Permission> es una clase abstracta. Por consiguiente, debe usar las clases derivadas para definir los permisos en los objetos correspondientes. Para cada objeto se define una clase derivada de permiso.  
  
|Objeto|Clase|  
|------------|-----------|  
|<xref:Microsoft.AnalysisServices.Database>|<xref:Microsoft.AnalysisServices.DatabasePermission>|  
|<xref:Microsoft.AnalysisServices.DataSource>|<xref:Microsoft.AnalysisServices.DataSourcePermission>|  
|<xref:Microsoft.AnalysisServices.Dimension>|<xref:Microsoft.AnalysisServices.DimensionPermission>|  
|<xref:Microsoft.AnalysisServices.Cube>|<xref:Microsoft.AnalysisServices.CubePermission>|  
|<xref:Microsoft.AnalysisServices.MiningStructure>|<xref:Microsoft.AnalysisServices.MiningStructurePermission>|  
|<xref:Microsoft.AnalysisServices.MiningModel>|<xref:Microsoft.AnalysisServices.MiningModelPermission>|  
  
 En la lista se muestran las posibles acciones habilitadas por permisos:  
  
|Acción|Valores|Explicación|  
|------------|------------|-----------------|  
|Procesar|{`true`, `false`}<br /><br /> Valor predeterminado = `false`|Si es `true`, los miembros pueden procesar el objeto y cualquier objeto contenido en él.<br /><br /> Los permisos de proceso no se aplican a los modelos de minería de datos. <xref:Microsoft.AnalysisServices.MiningModel> siempre se heredan los permisos <xref:Microsoft.AnalysisServices.MiningStructure>.|  
|Leer definición|{`None`, `Basic`, `Allowed`}<br /><br /> Valor predeterminado = `None`|Especifica si los miembros pueden leer la definición de datos (ASSL) asociada al objeto.<br /><br /> Si el valor es `Allowed`, los miembros pueden leer el ASSL asociado al objeto.<br /><br /> `Basic` y `Allowed` son heredadas por los objetos que se encuentran en el objeto. `Allowed` invalida `Basic` y `None`.<br /><br /> `Allowed` se requiere para usar DISCOVER_XML_METADATA en un objeto. `Basic` se requiere para crear objetos vinculados y cubos locales.|  
|Lectura|{`None`, `Allowed`}<br /><br /> Valor predeterminado =`None` (excepto en permisos de dimensión, donde el valor predeterminado =`Allowed`)|Especifica si los miembros disponen de acceso de lectura a los conjuntos de filas de esquema y contenido de datos.<br /><br /> `Allowed` proporciona acceso de lectura en una base de datos, lo que le permite detectar una base de datos.<br /><br /> `Allowed` en un cubo proporciona acceso de lectura a conjuntos de filas de esquema y acceso al contenido del cubo (a menos que se restrinja mediante <xref:Microsoft.AnalysisServices.CellPermission> y <xref:Microsoft.AnalysisServices.CubeDimensionPermission>).<br /><br /> `Allowed` en una dimensión concede permiso de lectura en todos los atributos de la dimensión (a menos que se restrinja mediante <xref:Microsoft.AnalysisServices.CubeDimensionPermission>). El permiso de lectura solamente se usa para la herencia estática a <xref:Microsoft.AnalysisServices.CubeDimensionPermission>. `None` en una dimensión oculta la dimensión y solo proporciona acceso al miembro predeterminado para los atributos agregables; se produce un error si la dimensión contiene un atributo no agregable.<br /><br /> `Allowed` en <xref:Microsoft.AnalysisServices.MiningModelPermission> concede permisos para ver los objetos en conjuntos de filas de esquema y para realizar combinaciones de predicciones.<br /><br /> **NoteAllowed** es necesario para leer o escribir en cualquier objeto en la base de datos.|  
|Escribir|{`None`, `Allowed`}<br /><br /> Valor predeterminado = `None`|Especifica si los miembros tienen acceso de escritura a los datos del objeto primario.<br /><br /> El acceso se aplica a las subclases <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.Cube> y <xref:Microsoft.AnalysisServices.MiningModel>. No se aplica a la base de datos <xref:Microsoft.AnalysisServices.MiningStructure> subclases, lo que genera un error de validación.<br /><br /> `Allowed` en <xref:Microsoft.AnalysisServices.Dimension> concede permiso de escritura en todos los atributos de la dimensión.<br /><br /> `Allowed` en <xref:Microsoft.AnalysisServices.Cube> concede permiso de escritura en las celdas del cubo de particiones definidas con el tipo de reescritura.<br /><br /> `Allowed` en <xref:Microsoft.AnalysisServices.MiningModel> concede permiso para modificar el contenido del modelo.<br /><br /> `Allowed` en un <xref:Microsoft.AnalysisServices.MiningStructure> tiene ningún significado concreto [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. **Nota:** escritura no puede establecerse en `Allowed` a menos que la lectura también se establece en `Allowed`|  
|Administrar **Nota:** solo en los permisos de base de datos|{`true`, `false`}<br /><br /> Valor predeterminado = `false`|Especifica si los miembros pueden administrar una base de datos.<br /><br /> `true` concede acceso a todos los objetos de una base de datos de miembros.<br /><br /> Un miembro puede tener permisos para administrar una base de datos concreta, pero no otras.|  
  
## <a name="see-also"></a>Vea también  
 [Autorizar el acceso a objetos y operaciones &#40;Analysis Services&#41;](../authorizing-access-to-objects-and-operations-analysis-services.md)  
  
  
