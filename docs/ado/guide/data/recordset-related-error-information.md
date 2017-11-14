---
title: "Información de Error relacionado con el conjunto de registros | Documentos de Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Recordset-related errors [ADO]
- errors [ADO], Recordset-related
ms.assetid: 7e103574-59ad-4790-b5f9-fa8d715e711e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 279fcc0564f433234cbac730465e2af06a7eb5e7
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="recordset-related-error-information"></a>Información de Error relacionado con el conjunto de registros
Durante el procesamiento por lotes, el **estado** propiedad de la **Recordset** objeto proporciona información acerca de los registros individuales en la **conjunto de registros**. Antes de una actualización por lotes tiene lugar, el **estado** propiedad de la **Recordset** refleja la información acerca de los registros para agregar, cambiar y eliminar. Después de **UpdateBatch** se ha llamado, el **estado** propiedad indica el éxito o fracaso de la operación. Mientras se desplaza por los registros en la **Recordset**, el valor de la **estado** cambios de propiedad para describir el estado del registro actual.

