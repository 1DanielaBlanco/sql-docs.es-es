---
title: Detección de tipos de parámetro con valores de tabla | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: eea5d45c4c21b740a3ea91ee27023129b33719b3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36106590"
---
# <a name="table-valued-parameter-type-discovery"></a>Detección de tipos de parámetros con valores de tabla
  El consumidor, es decir, la aplicación cliente mediante el [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor Native Client OLE DB, puede detectar el tipo de cada parámetro de comando si el texto del comando se ha proporcionado el proveedor OLE DB. Después de que se conoce el tipo de un parámetro con valores de tabla, el consumidor puede detectar la información de metadatos para cada columna del parámetro con valores de tabla.  
  
 La información de tipo de parámetros de procedimiento es compatible con ICommandWithParameters:: GetParameterInfo para la mayoría de los tipos de parámetro. A partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], con la introducción de tipos definidos por el usuario y la `xml` tipo de datos, el método GetParameterInfo no es suficiente para este propósito porque no era posible proporcionar información de tipo definido por el usuario (nombre, esquema, y catálogo) a través de ICommandWithParameters. Se definió una nueva interfaz, ISSCommandWithParameters, para proporcionar información de tipo extendido.  
  
 Para los parámetros con valores de tabla, también se usa la interfaz ISSCommandWithParameters para detectar información detallada. El cliente llama a ISSCommandWithParameters::GetParameterInfo después de preparar el objeto de comando. Para los parámetros con valores de tabla, el *wType* miembro de la estructura DBPARAMINFO está establecido en DBTYPE_TABLE por el proveedor. El *ulParamSize* campo de la estructura DBPARAMINFO tiene un valor de ~ 0.  
  
 El consumidor solicitará a continuación propiedades adicionales (nombre de catálogo del tipo de parámetro con valores de tabla, nombre de esquema del tipo de parámetro con valores de tabla, nombre de tipo de parámetro con valores de tabla, ordenar las columnas y las columnas predeterminadas) utilizando ISSCommandWithParamters:: GetParameterProperties.  
  
 Después de que se conoce el nombre de tipo, para recuperar la información de columna individuales, el consumidor debe llamar a IOpenRowset::OpenRowsetor obtener el conjunto de filas DBSCHEMA_TABLE_TYPE_COLUMNS especificando el nombre del tipo de parámetro con valores de tabla como el nombre de tabla.  
  
## <a name="see-also"></a>Vea también  
 [Parámetros con valores de tabla &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Usar parámetros con valores de tabla &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  