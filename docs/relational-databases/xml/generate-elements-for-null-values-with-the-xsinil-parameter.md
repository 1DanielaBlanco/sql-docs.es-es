---
title: Generar elementos para valores NULL mediante el parámetro XSINIL | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, null values
- null values [SQL Server], XML
- ELEMENTS directive
- XSINIL parameter
ms.assetid: 2dbc4e48-1cae-4d83-b371-3265da9687cc
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 66086f046b4ea95325747131edcea5f8868e1562
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47702483"
---
# <a name="generate-elements-for-null-values-with-the-xsinil-parameter"></a>Generar elementos para valores NULL mediante el parámetro XSINIL
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  La directiva **ELEMENTS** genera XML en el cual cada valor de columna se asigna a un elemento del XML. Si el valor de la columna es NULL, no se agrega ningún elemento. Al especificar el parámetro **XSINIL** opcional en la directiva ELEMENTS, se puede solicitar que también se cree un elemento para el valor NULL. En este caso, se devuelve un elemento que tiene el atributo **xsi:nil** establecido en TRUE para cada valor de columna NULL.  
  
## <a name="see-also"></a>Ver también  
 [Usar el modo RAW con FOR XML](../../relational-databases/xml/use-raw-mode-with-for-xml.md)  
  
  
