---
title: Reducir (tipo de datos geography) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Reduce_TSQL
- Reduce
dev_langs:
- TSQL
helpviewer_keywords:
- Reduce method
ms.assetid: c5dfa8c1-6764-41d8-9150-f3cb30633d3e
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c5b174f3f4b8daf99c402b110ba10d95345783d7
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="reduce-geography-data-type-"></a>Reduce (tipo de datos Geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Devuelve una aproximación de la determinada **geography** instancia genera al aplicar el algoritmo de Douglas-Peucker a la instancia con la tolerancia indicada.  
  
 Esto **geography** admite el método de tipo de datos **FullGlobe** instancias o instancias espaciales mayores que un hemisferio.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
.Reduce ( tolerance )  
```  
  
## <a name="arguments"></a>Argumentos  
  
|||  
|-|-|  
|Término|Definición|  
|*tolerancia*|Es un valor de tipo **float**. *tolerancia* es la tolerancia como entrada para el algoritmo de Douglas-Peucker. *tolerancia* debe ser un número positivo.|  
  
## <a name="return-types"></a>Tipos devueltos  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]tipo de valor devuelto: **geography**  
  
 Tipo de valor devuelto de CLR: **SqlGeography**  
  
## <a name="remarks"></a>Comentarios  
 Para los tipos de colección, este algoritmo funciona independientemente en cada **geography** contenidos en la instancia. Este algoritmo no modifica **punto** instancias.  
  
 Este método intentará conservar los puntos de conexión de **LineString** instancias, pero puede que no hacerlo para mantener un resultado válido.  
  
 Si `Reduce()` se llama con un valor negativo, este método generará una **ArgumentException**. Las tolerancias utilizadas en `Reduce()` deben ser números positivos.  
  
 Las obras de algoritmo de Douglas-Peucker en cada curva o anillo de la **geography** instancia mediante la eliminación de todos los puntos excepto el punto inicial y final. Cada punto quitado se agrega de nuevo entonces, comenzando con el punto periférico más lejano, hasta que no hay ningún punto más de *tolerancia* del resultado. A continuación, el resultado se convierte en válido, si es necesario, cuando se garantiza un resultado válido.  
  
 En [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], este método se ha ampliado a **FullGlobe** instancias.  
  
 Este método no es preciso.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se crea una instancia sencilla de `LineString` y se utiliza `Reduce()` para simplificar la instancia.  
  
```  
DECLARE @g geography = 'LineString(120 45, 120.1 45.1, 199.9 45.2, 120 46)'  
SELECT @g.Reduce(10000).ToString()  
```  
  
## <a name="see-also"></a>Vea también  
 [Métodos extendidos en instancias de Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  

