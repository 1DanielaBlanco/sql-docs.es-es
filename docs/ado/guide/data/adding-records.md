---
title: Agregar registros | Documentos de Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, editing data
- editing data [ADO], AddNew method
- editing data [ADO], adding data
ms.assetid: dd34669e-6f06-403b-9241-1c85c82aecc2
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7a1d367e572a7839b6a5d54b1c6460716aa09160
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35271064"
---
# <a name="adding-records-to-a-recordset"></a>Agregar registros a un conjunto de registros
Use la **AddNew** método para crear e inicializar un nuevo registro en una existente **conjunto de registros**. Puede usar el **admite** método con un **CursorOptionEnum** valo **adAddNew** para comprobar si puede agregar registros al actual **delconjuntoderegistros** objeto.

 Después de llamar a la **AddNew** método, el nuevo registro se convierte en el registro actual y permanece actual después de llamar a la **actualización** método. Si el **Recordset** objeto no admite marcadores, no podría tener acceso al registro nuevo cuando se mueva a otro registro. Por lo tanto, según el tipo de cursor, tendrá que llamar a la **Requery** método para hacer que el nuevo registro sea accesible.

 Si se llama a **AddNew** mientras se edita el registro actual o al agregar un nuevo registro, ADO llama el **actualización** método para guardarlos cambios y, a continuación, crea el nuevo registro.

 Esta sección contiene los temas siguientes.

-   [Agregar registros mediante AddNew (método)](../../../ado/guide/data/adding-records-using-addnew.md)

-   [Agregar varios campos y valores](../../../ado/guide/data/adding-multiple-fields.md)

-   [Determinar el modo de edición](../../../ado/guide/data/determining-edit-mode.md)

-   [Uso de AddNew de inmediato y modos de lote](../../../ado/guide/data/using-addnew-in-immediate-and-batch-modes.md)
