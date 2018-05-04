---
title: Tratamiento de errores | Microsoft Docs
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
- reporting errors [ADO]
- errors [ADO]
- ADO, error handling
ms.assetid: 4909e413-f3b0-4183-8ad3-67b1434df742
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e302e38ee983f8057aa2ce1be321e195abe0afbb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="error-handling"></a>Tratamiento de errores
ADO utiliza varios métodos diferentes para notificar a una aplicación de errores que se producen. Esta sección describen los tipos de errores que pueden producirse cuando se utiliza ADO y cómo se notifica a la aplicación. Se termina con unas sugerencias sobre cómo controlar los errores.  
  
## <a name="how-does-ado-report-errors"></a>¿Cómo ADO notifica los errores?  
 ADO notifica los errores de varias maneras:  
  
-   Los errores de ADO generan un error en tiempo de ejecución. Controlar un error de ADO de la misma manera que lo haría con cualquier otro error de tiempo de ejecución, como el uso de un **On Error** instrucción en Visual Basic.  
  
-   El programa puede recibir errores de OLE DB. ¡Error de OLE DB genera un error de tiempo de ejecución también.  
  
-   Si el error es específico de su proveedor de datos, uno o varios **Error** objetos se colocan en la **errores** colección de la **conexión** objeto que se usó para acceder a los datos almacenar cuando se produjo el error.  
  
-   Si el proceso que desencadenó un evento también produce un error, información de error se coloca en un **Error** del objeto y se pasa como parámetro al evento. Vea [controlar eventos de ADO](../../../ado/guide/data/handling-ado-events.md) para obtener más información acerca de los eventos.  
  
-   Problemas que se producen al procesar por lotes las actualizaciones u otras operaciones masivas que implican un **Recordset** puede indicarse mediante la **estado** propiedad de la **conjunto de registros**. Por ejemplo, pueden especificar por infracciones de restricción de esquema o permisos insuficientes **RecordStatusEnum** valores.  
  
-   Problemas que se producen implicando a un determinado **campo** en el registro actual también se indican mediante el **estado** propiedad de cada **campo** en la **campos**  colección de la **registro** o **conjunto de registros**. Por ejemplo, se pueden especificar las actualizaciones que no se pudieron completar o tipos de datos incompatibles por **FieldStatusEnum** valores.  
  
 Esta sección contiene los temas siguientes.  
  
-   [Errores de tiempo de ejecución de ADO](../../../ado/guide/data/ado-errors.md)  
  
-   [Errores del proveedor](../../../ado/guide/data/provider-errors.md)  
  
-   [Información de Error relacionado con el campo](../../../ado/guide/data/field-related-error-information.md)  
  
-   [Información de Error relacionado con el conjunto de registros](../../../ado/guide/data/recordset-related-error-information.md)  
  
-   [Control de errores en otros lenguajes](../../../ado/guide/data/handling-errors-in-other-languages.md)  
  
-   [Anticipación de errores](../../../ado/guide/data/anticipating-errors.md)
