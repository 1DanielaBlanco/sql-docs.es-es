---
title: SaveOptionsEnum | Documentos de Microsoft
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
apitype: COM
f1_keywords:
- SaveOptionsEnum
helpviewer_keywords:
- SaveOptionsEnum enumeration [ADO]
ms.assetid: 59339100-6e29-48d1-aea3-6873796d186b
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 502b6cf58647b7fe3a2b8dd8e7b627e60869cb43
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="saveoptionsenum"></a>SaveOptionsEnum
Especifica si se debe crear un archivo o sobrescribir al guardar desde un [flujo](../../../ado/reference/ado-api/stream-object-ado.md) objeto. Los valores pueden ser **adSaveCreateNotExist** o **adSaveCreateOverWrite**...  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adSaveCreateNotExist**|1|Predeterminado: Crea un nuevo archivo si el archivo especificado por el *FileName* parámetro aún no existe.|  
|**adSaveCreateOverWrite**|2|Sobrescribe el archivo con los datos de abiertos actualmente **flujo** objeto, si el archivo especificado por el *Filename* parámetro ya existe. Si el archivo especificado por el *nombre de archivo* no existe el parámetro, se crea un nuevo archivo.|  
  
## <a name="adowfc-equivalent"></a>Equivalente ADO/WFC  
 Estas constantes no tienen equivalentes ADO/WFC.  
  
## <a name="applies-to"></a>Se aplica a  
 [Método SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)
