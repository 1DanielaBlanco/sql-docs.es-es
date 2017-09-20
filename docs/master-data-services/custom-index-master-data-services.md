---
title: "Índice personalizado (Master Data Services) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c57bf8b8-55a6-4b6c-9adb-91b5f4f1ee3c
caps.latest.revision: 9
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 2347f26d041c15142487420440a470f87a822e3e
ms.contentlocale: es-es
ms.lasthandoff: 09/07/2017

---
# <a name="custom-index-master-data-services"></a>Índice personalizado (Master Data Services)
  Los índices personalizados crean un índice no agrupado en un atributo (índice único) o en una lista de atributos (índice compuesto) de una entidad. Normalmente los índices mejoran el rendimiento del proceso de consulta. Para obtener más información sobre los índices de SQL Server, consulte [Índices](../relational-databases/indexes/indexes.md).  
  
## <a name="type-of-indexes"></a>Tipo de índices  
 Puede crear los siguientes tipos de índices personalizados para cada entidad.  
  
-   Índice único  
  
-   Índice no único  
  
 Un índice único garantiza que la columna indizada no contenga valores duplicados. En los índices únicos compuestos, el índice garantiza que cada combinación de valores de la lista de atributos seleccionados sea única. No se puede crear un índice único si existen valores duplicados para los atributos seleccionados.  
  
## <a name="rules"></a>Reglas  
 Las reglas siguientes se aplican a los índices personalizados, tanto únicos como no únicos.  
  
-   Para crear un índice personalizado, asegúrese de seleccionar al menos un atributo.  
  
-   Si intenta guardar un índice que tenga la misma lista de atributos y marca de unicidad que otro índice, no se podrá guardar. Aparece un error.  
  
    > [!NOTE]  
    >  MDS crea automáticamente índices para determinados atributos (como los DBA y el código). Esto significa que no se puede crear otro índice que contenga uno de estos atributos y ningún otro más.  
  
-   Los atributos se pueden incluir en más de un índice personalizado siempre que haya al menos un atributo diferente en los otros índices. De lo contrario, los índices son iguales.  
  
-   Si crea un índice que contenga muchos atributos o atributos de gran tamaño y el tamaño total de los atributos seleccionados supera el tamaño de clave de índice máximo (900 bytes), no se puede guardar el índice.  
  
-   Se puede crear un índice personalizado en los atributos de miembro hoja, excluidos los atributos de archivo.  
  
-   Si quiere eliminar un atributo incluido en un índice personalizado, se aplica lo siguiente.  
  
    -   Si el índice se crea en un solo atributo (índice único), tanto el atributo como el índice se eliminarán.  
  
    -   Si el índice se crea en más de un atributo (índice compuesto), el atributo no se puede eliminar hasta que edite el índice.  
  
-   No se puede cambiar el tipo de un atributo incluido en un índice personalizado.  
  
## <a name="related-tasks"></a>Tareas relacionadas  
  
|Descripción de la tarea|Tema|  
|----------------------|-----------|  
|Creación de un índice|[Creación de un índice personalizado &#40;Master Data Services&#41;](../master-data-services/create-an-index-master-data-services.md)|  
|Editar y eliminar un índice|[Editar y eliminar un índice &#40;Master Data Services&#41;](../master-data-services/edit-and-delete-an-index-master-data-services.md)|  
  
  
