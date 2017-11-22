---
title: "Clone (método) (ADO) | Documentos de Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Recordset20::Clone
- Recordset20::raw_Clone
helpviewer_keywords: Clone method [ADO]
ms.assetid: ad49265f-1c05-4271-9bbf-7c00010ac18c
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 34f8e0161fa85ec497ec6a1e6b414691161ff7a0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="clone-method-ado"></a>Clone (método) (ADO)
Crea un duplicado [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objeto a partir de una existente **Recordset** objeto. Opcionalmente, especifica que la clonación sea de solo lectura.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Set rstDuplicate = rstOriginal.Clone (LockType)  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un **Recordset** referencia de objeto.  
  
#### <a name="parameters"></a>Parámetros  
 *rstDuplicate*  
 Una variable de objeto que identifica el duplicado **Recordset** objeto que se va a crear.  
  
 *rstOriginal*  
 Una variable de objeto que identifica el **Recordset** objeto duplicado.  
  
 *LockType*  
 Opcional. A [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) valor que especifica el tipo de bloqueo de la versión original **Recordset**, o de solo lectura **conjunto de registros**. Los valores válidos son **adLockUnspecified** o **adLockReadOnly**.  
  
## <a name="remarks"></a>Comentarios  
 Use la **clon** duplicados de método para crear varios **Recordset** objetos, especialmente si desea mantener más de un registro actual en un determinado conjunto de registros. Mediante el **clon** método es más eficaz que crear y abrir un nuevo **Recordset** objeto que usa la misma definición que el original.  
  
 El [filtro](../../../ado/reference/ado-api/filter-property.md) propiedad del original **Recordset**, si existe, no se aplicará al clon. Establecer el **filtro** propiedad del nuevo **Recordset** para filtrar los resultados. La manera más sencilla de copiar cualquier existente **filtro** valor es asignarlo directamente, como se indica a continuación.  
  
```  
rsNew.Filter = rsOriginal.Filter  
```  
  
 El registro actual de un clon recién creado se establece en el primer registro.  
  
 Los cambios que realice a uno **Recordset** objeto están visibles en todos sus duplicados, independientemente del tipo de cursor. Sin embargo, después de ejecutar [Requery](../../../ado/reference/ado-api/requery-method.md) en el original **Recordset**, los clones ya no se sincronizarán con el original.  
  
 Cierre el original **Recordset** no se cierran sus copias, ni tampoco cerrar cerrar una copia del original o cualquiera de las demás copias.  
  
 Solo puede clonar una **Recordset** objeto que admite marcadores. Los valores de marcador son intercambiables; es decir, una referencia de marcador de un **Recordset** objeto hace referencia al mismo registro en cualquiera de sus clones.  
  
 Algunos **Recordset** eventos que se activan también se producirán en todos los **Recordset** clones. Sin embargo, puesto que el registro actual puede variar entre clonar **conjuntos de registros**, los eventos no pueden ser válidos para la clonación. Por ejemplo, si cambia un valor de un campo, un [WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md) evento se producirá en los cambios **Recordset** y en todos los duplicados. El *campos* parámetro de la **WillChangeField** eventos de clonada **Recordset** (donde no se ha realizado el cambio) hará referencia a los campos del registro actual de la clonación lo que puede ser un registro diferente que el registro actual del original **Recordset** donde se produjo el cambio.  
  
 En la tabla siguiente proporciona una lista completa de todos los **Recordset** eventos. Indica si son válidos y desencadenadas para los clones de conjunto de registros generados mediante la **clon** método.  
  
|Evento|¿Se desencadena en los duplicados?|  
|-----------|--------------------------|  
|[EndOfRecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|No|  
|[FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|No|  
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md)|No|  
|[FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Sí|  
|[MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|No|  
|[RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Sí|  
|[RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|No|  
|[WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Sí|  
|[WillChangeRecord](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Sí|  
|[WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|No|  
|[WillMove](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|No|  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto de conjunto de registros (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo del método Clone (VB)](../../../ado/reference/ado-api/clone-method-example-vb.md)   
 [Ejemplo del método Clone (VBScript)](../../../ado/reference/ado-api/clone-method-example-vbscript.md)   
 [Ejemplo del método Clone (VC ++)](../../../ado/reference/ado-api/clone-method-example-vc.md)   
