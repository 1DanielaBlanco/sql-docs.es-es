---
title: Conjuntos de registros filtrados y jerárquicos persistentes | Documentos de Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- filtered Recordset persistence [ADO]
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: d01aeb4d-4e43-450b-b3f2-0c27eaaf9f86
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d995e0d35f355f1d1b41fd0c6bcacd93da5b1b22
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="persisting-filtered-and-hierarchical-recordsets"></a>Almacenar conjuntos de registros filtrados y jerárquicos
Si el [filtro](../../../ado/reference/ado-api/filter-property.md) propiedad está en vigor para la **Recordset**, se guardan únicamente las filas accesibles con el filtro. Si el **Recordset** es jerárquico, el elemento secundario actual **Recordset** y sus elementos secundarios se guardan, incluida la primaria **conjunto de registros**. Si el **guardar** método de un elemento secundario **Recordset** es llama, el elemento secundario y todos sus elementos secundarios se guardan, pero el elemento primario no lo es. Para obtener más información acerca de jerárquica **conjuntos de registros**, consulte [dar forma a datos](../../../ado/guide/data/data-shaping.md).  
  
> [!NOTE]
>  Existen algunas limitaciones cuando se guarda jerárquica **conjuntos de registros** (formas de datos) en formato XML. Para obtener más información, consulte [almacenar registros en formato XML](../../../ado/guide/data/persisting-records-in-xml-format.md).
