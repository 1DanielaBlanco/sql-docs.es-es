---
title: Propiedades del catálogo de texto completo (tablas / página vistas) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-search
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.fulltextsearch.ftcatalogproperties.tablesviews.f1
ms.assetid: 2d45fcd2-0f0f-4167-9027-316d6696c106
caps.latest.revision: 25
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 0954fcb44358599314c9993fa53fcfad8dec73ec
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36202783"
---
# <a name="full-text-catalog-properties-tables-and-views-page"></a>Propiedades del catálogo de texto completo (Tablas/página Vistas)
  Utilice esta página de diálogo para ver o modificar las tablas y vistas asignadas al catálogo de texto completo.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Todos los objetos de tabla/vista apto en esta base de datos**  
 Muestra las tablas y vistas que disponen de un único índice definido, pero que todavía no forman parte del catálogo de texto completo. Para seleccionar una tabla o vista y asignársela al catálogo, seleccione los elementos en el cuadro de lista y presione el botón "->".  
  
 **Objetos de tabla o vista asignados al catálogo**  
 Muestra las tablas y vistas actualmente asignadas al catálogo de texto completo  
  
## <a name="selected-object-properties"></a>Propiedades de los objetos seleccionados  
 **Propiedades del objeto seleccionado**  
 Muestra las propiedades del objeto seleccionado en el cuadro de lista de objetos asignados al catálogo.  
  
 **Índice único**  
 Muestra los índices únicos disponibles de la tabla o vista.  
  
 **Tabla está habilitada la función de texto completo**  
 Active esta casilla para habilitar el índice de texto completo en la tabla. Desactive esta casilla para deshabilitar el índice de texto completo.  
  
## <a name="eligible-columns-grid"></a>Cuadrícula de columnas elegibles  
  
|||  
|-|-|  
|**Columnas disponibles**|Muestra todas las columnas con indización de texto completo. Active una casilla para agregar una columna al índice de texto completo.|  
|**Idioma del separador de palabras de**|Muestra el idioma del separador de palabras.|  
|**Columna tipo de datos**|Muestra el nombre de la columna en la tabla que contiene el tipo de documento de la columna que aparece en **columnas disponibles** si la columna es una `varbinary(max)` o `image` columna.|  
|**Semántica estadística**|Seleccione si desea habilitar la indización semántica para la columna seleccionada. Para obtener más información, vea [Búsqueda semántica &#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md).<br /><br /> Si selecciona **Idioma** antes de seleccionar **Semántica estadística**y el idioma seleccionado no tiene un modelo semántico asociado, la casilla **Semántica estadística** está deshabilitada. Si selecciona **Semántica estadística** antes de seleccionar **Idioma**, los idiomas disponibles en el cuadro combinado desplegable estarán limitados a aquellos para los que exista un modelo de idioma semántico.|  
  
## <a name="track-changes"></a>Seguimiento de cambios  
  
|||  
|-|-|  
|**Automático**|El índice de texto completo se actualiza automáticamente cuando los datos de la tabla subyacente se modifican, se agregan o se eliminan.|  
|**Manual**|Cuando se modifica, se agregan o se eliminan en los datos indizados, datos [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] realiza un seguimiento de los cambios. Cuando está activado el seguimiento de cambios **Manual** , el índice no se actualiza automáticamente con estos cambios. En su lugar, un administrador puede aplicar los cambios manualmente utilizando un [ALTER FULLTEXT INDEX... START UPDATE POPULATION](/sql/t-sql/statements/alter-fulltext-index-transact-sql) instrucción.|  
|**No realizar seguimiento de cambios**|Con esta opción activa, no se registran los cambios realizados en los datos indizados del catálogo. Un administrador debe generar el índice utilizando FULLTEXT del ALTER INDICE con POBLACIÓN COMPLETA o la POBLACIÓN INCREMENTAL.|  
  
## <a name="see-also"></a>Vea también  
 [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)   
 [ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-catalog-transact-sql)   
 [Rellenar índices de texto completo](../relational-databases/indexes/indexes.md)  
  
  
