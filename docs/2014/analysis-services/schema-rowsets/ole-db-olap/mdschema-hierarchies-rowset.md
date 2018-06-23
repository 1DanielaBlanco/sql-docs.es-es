---
title: Conjunto de filas MDSCHEMA_HIERARCHIES | Documentos de Microsoft
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
api_name:
- MDSCHEMA_HIERARCHIES
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_HIERARCHIES rowset
ms.assetid: 2e5b2a81-366e-4d5b-af1e-1d372bf596d9
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e8c6fa75c935256235d64ad337500923b5974c68
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36113260"
---
# <a name="mdschemahierarchies-rowset"></a>Conjunto de filas MDSCHEMA_HIERARCHIES
  Describe cada jerarquía dentro de una dimensión determinada.  
  
## <a name="rowset-columns"></a>Columnas del conjunto de filas  
 El `MDSCHEMA_HIERARCHIES` filas contiene las columnas siguientes.  
  
|Nombre de columna|Indicador de tipo|Longitud|Descripción|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||El nombre del catálogo al que pertenece esta jerarquía. `NULL` si el proveedor no admite catálogos.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||No compatible|  
|`CUBE_NAME`|`DBTYPE_WSTR`||(Obligatorio) Nombre único del cubo al que pertenece la jerarquía.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`||Nombre único de la dimensión a la que pertenece esta jerarquía. Los proveedores que generan nombres únicos por calificación tienen delimitados todos los componentes del nombre.|  
|`HIERARCHY_NAME`|`DBTYPE_WSTR`||Es el nombre de la jerarquía. En blanco si solo hay una única jerarquía en la dimensión. Esto siempre tendrá un valor en [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`||Nombre único de la jerarquía.|  
|`HIERARCHY_GUID`|`DBTYPE_GUID`||No compatible|  
|`HIERARCHY_CAPTION`|`DBTYPE_WSTR`||Una etiqueta o título asociado a la jerarquía. Se utiliza principalmente para la presentación. Si no existe ningún título, se devuelve `HIERARCHY_NAME`. Si la dimensión no contiene una jerarquía o tiene únicamente una jerarquía, esta columna contendrá el nombre de la dimensión.|  
|`DIMENSION_TYPE`|`DBTYPE_I2`||El tipo de la dimensión. Los valores válidos son los siguientes:<br /><br /> -   `MD_DIMTYPE_UNKNOWN` (`0`)<br />-   `MD_DIMTYPE_TIME` (`1`)<br />-   `MD_DIMTYPE_MEASURE` (`2`)<br />-   `MD_DIMTYPE_OTHER` (`3`)<br />-   `MD_DIMTYPE_QUANTITATIVE` (`5`)<br />-   `MD_DIMTYPE_ACCOUNTS` (`6`)<br />-   `MD_DIMTYPE_CUSTOMERS` (`7`)<br />-   `MD_DIMTYPE_PRODUCTS` (`8`)<br />-   `MD_DIMTYPE_SCENARIO` (`9`)<br />-   `MD_DIMTYPE_UTILIY` (`10`)<br />-   `MD_DIMTYPE_CURRENCY` (`11`)<br />-   `MD_DIMTYPE_RATES` (`12`)<br />-   `MD_DIMTYPE_CHANNEL` (`13`)<br />-   `MD_DIMTYPE_PROMOTION` (`14`)<br />-   `MD_DIMTYPE_ORGANIZATION` (`15`)<br />-   `MD_DIMTYPE_BILL_OF_MATERIALS` (`16`)<br />-   `MD_DIMTYPE_GEOGRAPHY` (`17`)|  
|`HIERARCHY_CARDINALITY`|`DBTYPE_UI4`||Número de miembros de la jerarquía.|  
|`DEFAULT_MEMBER`|`DBTYPE_WSTR`||El miembro predeterminado de esta jerarquía. Éste es un nombre único. Cada jerarquía debe tener un miembro predeterminado.|  
|`ALL_MEMBER`|`DBTYPE_WSTR`||El miembro en el nivel superior del resumen.|  
|`DESCRIPTION`|`DBTYPE_WSTR`||Una descripción inteligible de la jerarquía. `NULL` si no existe ninguna descripción.|  
|`STRUCTURE`|`DBTYPE_I2`||Estructura de la jerarquía. Los valores válidos son los siguientes:<br /><br /> -   `MD_STRUCTURE_FULLYBALANCED` (`0`)<br />-   `MD_STRUCTURE_RAGGEDBALANCED` (`1`)<br />-   `MD_STRUCTURE_UNBALANCED` (`2`)<br />-   `MD_STRUCTURE_NETWORK` (`3`)|  
|`IS_VIRTUAL`|`DBTYPE_BOOL`||Siempre devuelve `False`.|  
|`IS_READWRITE`|`DBTYPE_BOOL`||Un booleano que indica si la columna Reescritura en la dimensión está habilitada.<br /><br /> Devuelve `TRUE` si la columna `Write Back to dimension` que representa esta jerarquía está habilitada.|  
|`DIMENSION_UNIQUE_SETTINGS`|`DBTYPE_I4`||Siempre devuelve `MDDIMENSIONS_MEMBER_KEY_UNIQUE` (`1`).|  
|`DIMENSION_MASTER_UNIQUE_NAME`|`DBTYPE_WSTR`||Siempre devuelve `NULL`.|  
|`DIMENSION_IS_VISIBLE`|`DBTYPE_BOOL`||Siempre devuelve `true`. Si la dimensión no está visible, no aparecerá en el conjunto de filas de esquema.|  
|`HIERARCHY_ORDINAL`|`DBTYPE_UI4`||El número ordinal de la jerarquía en todas las jerarquías del cubo.|  
|`DIMENSION_IS_SHARED`|`DBTYPE_BOOL`||Siempre devuelve `TRUE`.|  
|`HIERARCHY_IS_VISIBLE`|`DBTYPE_BOOL`||Un booleano que indica si la jerarquía está visible.<br /><br /> Devuelve `TRUE` si la jerarquía está visible; en caso contrario, `FALSE`.|  
|`HIERARCHY_ORIGIN`|`DBTYPE_UI2`||Una máscara de bits que determina el origen de la jerarquía:<br /><br /> -   `MD_USER_DEFINED` identifica las jerarquías definidas por el usuario y tiene un valor de `0x0000001`.<br />-   `MD_SYSTEM_ENABLED` identifica las jerarquías de atributo y tiene un valor de `0x0000002`.<br />-   `MD_SYSTEM_INTERNAL` identifica los atributos con ninguna jerarquía de atributo y tiene un valor de **0x0000004**.<br /><br /> Una jerarquía de atributo de elemento primario/secundario es `MD_USER_DEFINED` y `MD_SYSTEM_ENABLED`.|  
|`HIERARCHY_DISPLAY_FOLDER`|`DBTYPE_WSTR`||La ruta que se va a utilizar al mostrar la jerarquía en la interfaz de usuario. Un punto y coma (;) separará los nombres de carpeta. Las carpetas anidadas se indican mediante una barra diagonal inversa (\\).|  
|`INSTANCE_SELECTION`|`DBTYPE_UI2`||Una sugerencia a la aplicación cliente sobre cómo mostrar la jerarquía. Los valores válidos son los siguientes:<br /><br /> -   `MD_INSTANCE_SELECTION_NONE`<br />-   `MD_INSTANCE_SELECTION_DROPDOWN`<br />-   `MD_INSTANCE_SELECTION_LIST`<br />-   `MD_INSTANCE_SELECTION_FILTEREDLIST`<br />-   `MD_INSTANCE_SELECTION_MANDATORYFILTER`|  
|`GROUPING_BEHAVIOR`|`DBTYPE_I2`||Una enumeración que especifica el comportamiento de agrupación esperado de los clientes de esta jerarquía. A continuación se indican los posibles valores:<br /><br /> -   **EncourageGrouping** (1)<br />-   **DiscourageGrouping** (2)|  
|`STRUCTURE_TYPE`|`DBTYPE_WSTR`||Indica el tipo de jerarquía. Los valores válidos son los siguientes:<br /><br /> -   `Natural`<br />-   `Unnatural`<br />-   `Unknown`|  
  
 El conjunto de filas se ordena en `CATALOG_NAME`, `SCHEMA_NAME`, `CUBE_NAME`, `DIMENSION_UNIQUE_NAME`, `HIERARCHY_NAME`.  
  
## <a name="restriction-columns"></a>Columnas de restricción  
 El `MDSCHEMA_HIERARCHIES` se puede restringir el conjunto de filas en las columnas enumeradas en la tabla siguiente.  
  
|Nombre de columna|Indicador de tipo|Estado de restricción|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|Opcional.|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|Opcional.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Opcional.|  
|`DIMENSION_UNIQUE_NAME`|`DBTYPE_WSTR`|Opcional.|  
|`HIERARCHY_NAME`|`DBTYPE_WSTR`|Opcional.|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|Opcional.|  
|`HIERARCHY_ORIGIN`|`DBTYPE_UI2`|(Opcional) Una restricción predeterminada está en vigor en MD_USER_DEFINED y MD_SYSTEM_ENABLED.|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(Opcional) Mapa de bits con uno de los siguientes valores válidos:<br /><br /> -CUBO 1<br />-DIMENSIÓN DE 2<br /><br /> La restricción predeterminada es un valor de 1.|  
|`HIERARCHY_VISIBILITY`|`DBTYPE_UI2`|(Opcional) Mapa de bits con uno de los siguientes valores válidos:<br /><br /> -1 Visible<br />-2 no visible<br /><br /> La restricción predeterminada es un valor de 1.|  
  
## <a name="see-also"></a>Vea también  
 [OLE DB para los conjuntos de filas de esquema OLAP](ole-db-for-olap-schema-rowsets.md)  
  
  