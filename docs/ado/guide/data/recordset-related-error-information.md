---
title: Información de Error relacionado con el conjunto de registros | Documentos de Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset-related errors [ADO]
- errors [ADO], Recordset-related
ms.assetid: 7e103574-59ad-4790-b5f9-fa8d715e711e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b9a4f68dfffa07f79bdd53e380b68f55d3a01dfe
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="recordset-related-error-information"></a>Información de Error relacionado con el conjunto de registros
Durante el procesamiento por lotes, el **estado** propiedad de la **Recordset** objeto proporciona información acerca de los registros individuales en la **conjunto de registros**. Antes de una actualización por lotes tiene lugar, el **estado** propiedad de la **Recordset** refleja la información acerca de los registros para agregar, cambiar y eliminar. Después de **UpdateBatch** se ha llamado, el **estado** propiedad indica el éxito o fracaso de la operación. Mientras se desplaza por los registros en la **Recordset**, el valor de la **estado** cambios de propiedad para describir el estado del registro actual.
