---
title: Conjuntos de filas | Documentos de Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], about rowsets
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets
- OLE DB rowsets, about rowsets
- rowsets [OLE DB]
ms.assetid: 5e7b3cbe-3670-4e18-8172-2226e0b6b142
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: daa4edfaaf4339d03993f0e53375b8b406a99e86
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36197597"
---
# <a name="rowsets"></a>Conjuntos de filas
  Un conjunto de filas es el que contiene columnas de datos. Los conjuntos de filas son objetos centrales que permiten a todos los proveedores de datos OLE DB exponer los datos del conjunto de resultados en formato tabular.  
  
 Después de que un consumidor crea una sesión mediante el uso de la **IDBCreateSession::** método, el consumidor puede utilizar el **IOpenRowset** o **IDBCreateCommand** interfaz en la sesión que se va a crear un conjunto de filas. El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor Native Client OLE DB admite tanto de estas interfaces. Los dos métodos se describen aquí.  
  
-   Crear un conjunto de filas mediante una llamada a la **IOpenRowset:: OpenRowset** método.  
  
     Esto es equivalente a crear un conjunto de filas sobre una tabla única. Este método se abre y devuelve un conjunto de filas que incluye todas las filas de una tabla base única. Uno de los argumentos a **OpenRowset** es un identificador de tabla que identifica la tabla desde la que se va a crear el conjunto de filas.  
  
-   Crear un objeto de comando mediante una llamada a la **IDBCreateCommand:: CreateCommand** método.  
  
     El objeto de comando ejecuta los comandos que el proveedor admite. Con el proveedor OLE DB de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, el consumidor puede especificar cualquier instrucción [!INCLUDE[tsql](../../includes/tsql-md.md)], como una instrucción SELECT o una llamada a un procedimiento almacenado. Los pasos para crear un conjunto de filas utilizando un objeto de comando son:  
  
    1.  El consumidor llama el **IDBCreateCommand:: CreateCommand** método en la sesión que se va a obtener un objeto de comando que solicita la **ICommandText** interfaz en el objeto de comando. Esto **ICommandText** interfaz establece y recupera el texto del comando real. El consumidor rellena el comando de texto mediante una llamada a la **ICommandText:: SetCommandText** método.  
  
    2.  El usuario llama el **ICommand:: Execute** método en el comando. El objeto de conjunto de filas generado cuando se ejecuta el comando contiene el conjunto de resultados del comando.  
  
 El consumidor puede utilizar el **ICommandProperties** interfaz para obtener o establecer las propiedades del conjunto de filas devuelto por el comando ejecutado por el **ICommand:: Execute** interfaces. Las propiedades solicitadas normalmente son las interfaces que el conjunto de filas debe admitir. Además de las interfaces, el consumidor puede solicitar propiedades que modifican el comportamiento del conjunto de filas o la interfaz.  
  
 Conjuntos de filas con los consumidores liberan el **IRowset:: Release** método. Al liberar un conjunto de filas se liberan los identificadores de fila mantenidos por el consumidor en ese conjunto de filas. Al liberar un conjunto de filas no se liberan los descriptores de acceso. Si tiene una **IAccessor** interfaz, todavía tiene que liberarse.  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [Crear un conjunto de filas con IOpenRowset](creating-a-rowset-with-iopenrowset.md)  
  
-   [Crear conjuntos de filas con ICommand:: Execute](creating-rowsets-with-icommand-execute.md)  
  
-   [Propiedades y comportamientos de conjuntos de filas](rowset-properties-and-behaviors.md)  
  
-   [Conjuntos de filas y cursores de SQL Server](rowsets-and-sql-server-cursors.md)  
  
-   [Capturar filas](fetching-rows.md)  
  
-   [Capturar una única fila con IRow](fetching-a-single-row-with-irow.md)  
  
-   [Marcadores](bookmarks.md)  
  
-   [Actualizar datos en conjuntos de filas](updating-data-in-rowsets.md)  
  
## <a name="see-also"></a>Vea también  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  