---
title: Conjunto de filas MDSCHEMA_ACTIONS | Documentos de Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0b2e2967b1b01c56801235b88220ea13be3b8e65
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="mdschemaactions-rowset"></a>Conjunto de filas MDSCHEMA_ACTIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Describe las acciones que pueden estar disponibles para la aplicación cliente.  
  
## <a name="rowset-columns"></a>Columnas del conjunto de filas  
 El **MDSCHEMA_ACTIONS** filas contiene las columnas siguientes.  
  
|Nombre de columna|Indicador de tipo|Longitud|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||El nombre de la base de datos.|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||No compatible. Siempre contiene **VT_NULL**.|  
|**RESTRICCIONES OBLIGATORIAS CUBE_NAME**|**DBTYPE_WSTR**||Nombre del cubo al que pertenece esta acción.|  
|**NOMBREDEACCIÓN**|**DBTYPE_WSTR**||El nombre de esta acción.|  
|**ACTION_TYPE**|**DBTYPE_I4**||Un mapa de bits que se utiliza para especificar el método de activación de la acción. El archivo Msmd.h define las constantes de valor de bit siguientes para este mapa de bits:<br /><br /> **MDACTION_TYPE_URL** (**0 x 01**)<br /><br /> **MDACTION_TYPE_HTML** (**0 x 02**)<br /><br /> **MDACTION_TYPE_STATEMENT** (**0 x 04**)<br /><br /> **MDACTION_TYPE_DATASET** (**0 x 08**)<br /><br /> **MDACTION_TYPE_ROWSET** (**0 x 10**)<br /><br /> **MDACTION_TYPE_COMMANDLINE** (**0 x 20**)<br /><br /> **MDACTION_TYPE_PROPRIETARY** (**0 x 40**)<br /><br /> **MDACTION_TYPE_REPORT** (**0 x 80**)<br /><br /> **MDACTION_TYPE_DRILLTHROUGH** (**0 x 100**)|  
|**COORDENADAS**|**DBTYPE_WSTR**||Una expresión multidimensional (MDX) que especifica un objeto o una coordenada en el espacio multidimensional en el que se realiza la acción. La aplicación cliente es responsable de proporcionar el valor de esta columna de restricción.<br /><br /> El **CORDINATE** debe resolverse en el objeto especificado en **COORDINATE_TYPE**.|  
|**COORDINATE_TYPE**|**DBTYPE_I4**||Un mapa de bits que especifica cómo la **COORDINAR** interpreta la columna de restricción. El archivo Msmd.h define las constantes de valor de bit siguientes para este mapa de bits:<br /><br /> **MDACTION_COORDINATE_CUBE** (**1**)<br /><br /> **MDACTION_COORDINATE_DIMENSION** (**2**): se refiere a las jerarquías de dimensiones.<br /><br /> **MDACTION_COORDINATE_LEVEL** (**3**)<br /><br /> **MDACTION_COORDINATE_MEMBER** (**4**)<br /><br /> **MDACTION_COORDINATE_SET** (**5**)<br /><br /> **MDACTION_COORDINATE_CELL** (**6**)|  
|**ACTION_CAPTION**|**DBTYPE_WSTR**||El nombre de acción si no se ha especificado ningún título y no se ha especificado ninguna traducción en la DDL.<br /><br /> Si se especificaron un título o traducciones, y **CaptionIsMDX** es false, una de las siguientes cadenas:<br /><br /> -La traducción del idioma correspondiente.<br /><br /> -El título especificado si se ha encontrado ninguna traducción para el idioma especificado.<br /><br /> -El nombre de la acción, si se ha encontrado ninguna traducción y el título no se ha especificado en DDL.<br /><br /> Si se especificaron un título o traducciones, y **CaptionIsMDX** es true, la cadena resultante de buscar la traducción adecuada para el idioma especificado o la traslación especificada en el título DDL y calcular el fórmula para crear la cadena.<br /><br /> Si la acción se especifica en un script de MDX, no hay ninguna traducción y el título siempre se trata como expresión MDX.|  
|**DESCRIPTION**|**DBTYPE_WSTR**||Descripción fácil de comprender de la acción.|  
|**CONTENT**|**DBTYPE_WSTR**||La expresión o contenido de la acción que se va a ejecutar.|  
|**APLICACIÓN**|**DBTYPE_WSTR**||Nombre de la aplicación que se utilizará para ejecutar la acción.|  
|**INVOCACIÓN**|**DBTYPE_I4**||Información sobre cómo se debería invocar la acción:<br /><br /> **MDACTION_INVOCATION_INTERACTIVE** (**1**) indica una acción normal utilizada durante las operaciones normales. Este el valor predeterminado de esta columna.<br /><br /> **MDACTION_INVOCATION_ON_OPEN** (**2**) indica que la acción debe realizarse cuando se abre por primera vez el cubo.<br /><br /> **MDACTION_INVOCATION_BATCH** (**4**) indica que la acción se realiza como parte de una operación por lotes o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] tarea.<br /><br /> <br /><br /> Tenga en cuenta que estos valores de enumeración se definen en el archivo Msmd.h.|  
  
 El conjunto de filas está ordenado en **CATALOG_NAME**, **SCHEMA_NAME**, **restricciones obligatorias CUBE_NAME**, **ACTION_NAME**.  
  
> [!NOTE]  
>  Acciones de **MDACTION_TYPE_PROPRIETARY** tipo debe proporcionar un valor para el **aplicación** columna.  
  
## <a name="restriction-columns"></a>Columnas de restricción  
 El **MDSCHEMA_ACTIONS** se puede restringir el conjunto de filas en las columnas enumeradas en la tabla siguiente.  
  
|Nombre de columna|Indicador de tipo|Estado de restricción|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|Opcional|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|Opcional|  
|**RESTRICCIONES OBLIGATORIAS CUBE_NAME**|**DBTYPE_WSTR**|Obligatorio|  
|**NOMBREDEACCIÓN**|**DBTYPE_WSTR**|Opcional|  
|**ACTION_TYPE**|**DBTYPE_I4**|Opcional|  
|**COORDENADAS**|**DBTYPE_WSTR**|Obligatorio|  
|**COORDINATE_TYPE**|**DBTYPE_I4**|Obligatorio|  
|**INVOCACIÓN**|**DBTYPE_I4**|(Opcional) El **INVOCACIÓN** tiene como valor predeterminado en la columna de restricción en el valor de **MDACTION_INVOCATION_INTERACTIVE**. Para recuperar todas las acciones, use la **MDACTION_INVOCATION_ALL** valor en el **INVOCACIÓN** columna de restricción.|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(Opcional) La restricción predeterminada es un valor de 1. Un mapa de bits con uno de los siguientes valores válidos:<br /><br /> 1 CUBO<br /><br /> 2 DIMENSIÓN|  
  
> [!IMPORTANT]  
>  El **INVOCACIÓN** columna de restricción tiene un valor predeterminado de **MDACTION_INVOCATION_INTERACTIVE**. Cualquier conjunto de filas de esquema que no especifique explícitamente un valor para esta columna contiene únicamente las filas con este valor. Si desea que el conjunto de filas para contener todo el conjunto de acciones, utilice la **MDACTION_INVOCATION_ALL** constante en el **INVOCACIÓN** columna de restricción.  
  
 Las aplicaciones de cliente pueden definir más de un **ACTION_TYPE** mediante el operador OR.  
  
## <a name="remarks"></a>Comentarios  
 En la tabla siguiente se enumera los válido **COORDINAR** y **COORDINATE_TYPE** combinaciones.  
  
|Tipo de objeto COORDINATE|COORDINATE_TYPE|  
|----------------------------|----------------------|  
|**Cubo**|**MDACTION_COORDINATE_CUBE**|  
|**Dimensión**|**MDACTION_COORDINATE_DIMENSION**<br /><br /> **MDACTION_COORDINATE_LEVEL**<br /><br /> **MDACTION_COORDINATE_MEMBER**<br /><br /> **MDACTION_COORDINATE_SET**<br /><br /> **MDACTION_COORDINATE_CELL**|  
|**Jerarquía de**|**MDACTION_COORDINATE_DIMENSION**|  
|**Nivel**|**MDACTION_COORDINATE_LEVEL**|  
|**Miembro**|**MDACTION_COORDINATE_MEMBER**|  
|**Conjunto**|**MDACTION_COORDINATE_SET**|  
|**Celda**|**MDACTION_COORDINATE_CELL**|  
  
## <a name="see-also"></a>Vea también  
 [OLE DB para OLAP Schema Rowsets](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
