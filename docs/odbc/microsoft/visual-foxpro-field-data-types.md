---
title: Tipos de datos de campo de Visual FoxPro | Documentos de Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- field data types [ODBC]
- Visual FoxPro ODBC driver [ODBC], data types
ms.assetid: 50b733dc-679a-4b10-bc5d-98bb474dead2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7c1ae849d91962cb7d11ca8bac755665217fe1a2
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="visual-foxpro-field-data-types"></a>Tipos de datos de campo de Visual FoxPro
En la tabla siguiente se enumera los valores para la *FieldType* argumento en ALTER TABLE y CREATE TABLE e indica si *nFieldWidth* y *nPrecision* argumentos son Obligatorio.  
  
|*FieldType*|*NFieldWidth*|*nPrecision*|Description|  
|-----------------|-------------------|------------------|-----------------|  
|B|-|d|Doble|  
|C|N|-|Campo de caracteres de ancho*n*|  
|D|-|-|Date|  
|F|N|d|Flotante campo numérico de ancho * n * con *d.* posiciones decimales|  
|G|-|-|General|  
|I|-|-|Integer|  
|L|-|-|Lógico|  
|M|-|-|Memorándum|  
|N|N|d|Campo numérico de ancho * n * con *d.* posiciones decimales|  
|T|-|-|DateTime|  
|S|-|-|Moneda|

