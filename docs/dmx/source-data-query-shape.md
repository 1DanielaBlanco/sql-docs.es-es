---
title: FORMA (DMX) | Documentos de Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SHAPE
dev_langs:
- DMX
helpviewer_keywords:
- SHAPE statement
- multiple data sources
ms.assetid: b9526ec2-40bc-4bf5-b4e5-774f71075065
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: dcd4940769fc52852b1d48feb453f1393c754084
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="ltsource-data-querygt---shape"></a>&lt;consulta de origen de datos&gt; -forma
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Combina consultas de varios orígenes de datos en una única tabla jerárquica (es decir, una tabla con tablas anidadas), que se convierte en la tabla de caso para el modelo de minería de datos.  
  
 La sintaxis completa de la **forma** comandos se documentan en el [!INCLUDE[msCoName](../includes/msconame-md.md)] Kit de desarrollo de Software (SDK) de Data Access Components (MDAC).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
SHAPE {<master query>}  
APPEND ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS <column table name>  
[  
     ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS < column table name>  
...  
]       
```  
  
## <a name="arguments"></a>Argumentos  
 *consulta maestro*  
 Consulta que devuelve la tabla primaria.  
  
 *consulta de tabla secundaria*  
 Consulta que devuelve la tabla anidada.  
  
 *columna principal*  
 Columna de la tabla primaria que sirve para identificar filas secundarias a partir del resultado de una consulta de tabla secundaria.  
  
 *columna secundaria*  
 Columna de la tabla secundaria que sirve para identificar la fila primaria a partir del resultado de una consulta de la base de datos maestra.  
  
 *nombre de columna de tabla*  
 Nombre de columna que se acaba de anexar en la tabla primaria para la tabla anidada.  
  
## <a name="remarks"></a>Comentarios  
 Debe ordenar las consultas por la columna que relaciona la tabla primaria con la tabla secundaria.  
  
## <a name="examples"></a>Ejemplos  
 Puede usar el siguiente ejemplo en un [INSERT INTO &#40; DMX &#41;](../dmx/insert-into-dmx.md) instrucción para entrenar un modelo que contiene una tabla anidada. Las dos tablas de la **forma** instrucción se relacionan a través de la **OrderNumber** columna.  
  
```  
SHAPE {  
    OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber  
    FROM vAssocSeqOrders ORDER BY OrderNumber')  
} APPEND (  
    {OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber, model FROM   
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}  
  RELATE OrderNumber to OrderNumber)   
```  
  
## <a name="see-also"></a>Vea también  
 [&#60; consulta de origen de datos &#62;](../dmx/source-data-query.md)   
 [Extensiones de minería de datos &#40; DMX &#41; Instrucciones de definición de datos](../dmx/dmx-statements-data-definition.md)   
 [Extensiones de minería de datos &#40; DMX &#41; Instrucciones de manipulación de datos](../dmx/dmx-statements-data-manipulation.md)   
 [Extensiones de minería de datos &#40; DMX &#41; Referencia de instrucciones](../dmx/data-mining-extensions-dmx-statements.md)  
  
  

