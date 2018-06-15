---
title: La propiedad de proveedor (ADO) | Documentos de Microsoft
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
- Connection15::get_Provider
- Connection15::PutProvider
- Connection15::put_Provider
- Connection15::GetProvider
- Connection15::Provider
helpviewer_keywords:
- Provider property [ADO]
ms.assetid: 0ff70e72-0061-4ffc-90fb-e3ea23129bb2
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3491d76d0ba032cc9a8887f146bf9605aaf98772
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35280874"
---
# <a name="provider-property-ado"></a>Propiedad de proveedor (ADO)
Indica el nombre del proveedor para un [conexión](../../../ado/reference/ado-api/connection-object-ado.md) objeto.  
  
## <a name="settings-and-return-values"></a>Configuración y valores devueltos  
 Establece o devuelve un **cadena** valor que indica el nombre del proveedor.  
  
## <a name="remarks"></a>Notas  
 Use la **proveedor** propiedad para establecer o devolver el nombre del proveedor para una conexión. Esta propiedad también puede establecerse mediante el contenido de la [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) propiedad o el *ConnectionString* argumento de la [abiertos](../../../ado/reference/ado-api/open-method-ado-connection.md) método; sin embargo, al especificar un proveedor en más de un lugar mientras se llama el **abiertos** método puede tener resultados imprevisibles. Si no se especifica ningún proveedor, la propiedad valor predeterminado será MSDASQL ([proveedor Microsoft OLE DB para ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)).  
  
 El **proveedor** propiedad es de lectura/escritura cuando la conexión está cerrada y de solo lectura cuando se abre. El valor no surtirá efecto hasta que abra la **conexión** objeto o acceso a la [propiedades](../../../ado/reference/ado-api/properties-collection-ado.md) colección de la **conexión** objeto. Si el valor no es válido, se produce un error.  
  
## <a name="applies-to"></a>Se aplica a  
 [Objeto de conexión (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo Provider y DefaultDatabase propiedades (VB)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Ejemplo Provider y DefaultDatabase propiedades (VB)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Proveedor Microsoft OLE DB para ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)   
 [Apéndice A: Proveedores](../../../ado/guide/appendixes/appendix-a-providers.md)
