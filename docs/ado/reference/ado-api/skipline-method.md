---
title: Método SkipLine | Documentos de Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_SkipLine
- _Stream::SkipLine
helpviewer_keywords:
- Skipline method [ADO]
ms.assetid: 0abc00fe-ee09-4c8e-b1f2-48ee9c5f3329
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b5a2c6c5808abdcb13acb00c967ef35eeb943148
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282054"
---
# <a name="skipline-method"></a>Método SkipLine
Omite una línea completa al leer un texto [flujo](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Stream.SkipLine  
```  
  
## <a name="remarks"></a>Notas  
 Se omiten todos los caracteres hasta el siguiente separador de línea. De forma predeterminada, el [separador de línea](../../../ado/reference/ado-api/lineseparator-property-ado.md) es **adCRLF**. Si intenta omitir [sobrecargas eléctricas](../../../ado/reference/ado-api/eos-property.md), la posición actual se mantendrá en **sobrecargas eléctricas**.  
  
 El **SkipLine** método se utiliza con secuencias de texto ([tipo](../../../ado/reference/ado-api/type-property-ado-stream.md) es **adTypeText**).  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto de secuencia (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
