---
title: Proveedor de persistencia de Microsoft OLE DB (proveedor de servicios de ADO) | Documentos de Microsoft
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
- providers [ADO], OLE DB persistence provider
- persistence provider [ADO]
- OLE DB persistence provider [ADO]
ms.assetid: e75ef0dc-2016-4fcc-8918-23311c0d4e02
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d612484c8200a33be44e9b8b8ed230866be9ab95
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="microsoft-ole-db-persistence-provider-overview"></a>Información general sobre el proveedor de persistencia de Microsoft OLE DB
El proveedor de persistencia de Microsoft OLE DB permite guardar un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objeto en un archivo y posteriormente restaurar que **Recordset** objeto desde el archivo. Información de esquema, datos y se conservan los cambios pendientes.

 Puede guardar la **Recordset** en el formato propietario Advanced Data Table grama (ADTG) o en el formato de lenguaje de marcado Extensible (XML) abierto.

## <a name="provider-keyword"></a>Palabra clave del proveedor
 Para invocar este proveedor, especifique la siguiente palabra clave y valor en la cadena de conexión.

```
"Provider=MSPersist"
```

## <a name="errors"></a>Errores
 Los errores siguientes emitidos por este proveedor se pueden detectar en la aplicación.

|Constante|Description|
|--------------|-----------------|
|E_BADSTREAM|El archivo abierto no tiene un formato válido (es decir, el formato no es ADTG o XML).|
|E_CANTPERSISTROWSET|El **Recordset** objeto guardado tiene características que impiden que se va a almacenar.|

## <a name="remarks"></a>Comentarios
 El proveedor de persistencia de Microsoft OLE DB no expone ninguna propiedad dinámica.

 Actualmente, sólo parametrizar jerárquica **Recordset** no se pueden guardar los objetos.

 Para obtener más información acerca del almacenamiento persistente **Recordset** los objetos, vea [persistencia de conjunto de registros](../../../ado/guide/data/more-about-recordset-persistence.md).

 Cuando se utiliza una secuencia para abrir un **conjunto de registros,** no debería haber ningún parámetro especificada distinto el *origen* parámetro de la **abrir** método.

## <a name="see-also"></a>Vea también
[Proveedor de persistencia de Microsoft OLE DB (proveedor de servicios ADO)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)
