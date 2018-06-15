---
title: Append (método) (vistas ADOX) | Documentos de Microsoft
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
- Views::raw_Append
- Views::Append
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: 6070fd58-3237-4c77-a966-5b39ce5d57e4
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a524be12a721d86e0e5afd1029f486ca7c8ecaa9
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35285214"
---
# <a name="append-method-adox-views"></a>Append (método) (vistas ADOX)
Crea un nuevo [vista](../../../ado/reference/adox-api/view-object-adox.md) objeto y lo anexa a la [vistas](../../../ado/reference/adox-api/views-collection-adox.md) colección.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Views.Append Name, Command  
```  
  
#### <a name="parameters"></a>Parámetros  
 *Nombre*  
 A **cadena** valor que especifica el nombre de la vista para crear.  
  
 *Command*  
 ADO [comando](../../../ado/reference/ado-api/command-object-ado.md) objeto que representa la vista para crear.  
  
## <a name="remarks"></a>Notas  
 Crea una nueva vista del origen de datos con el nombre y los atributos especificados en el **comando** objeto.  
  
 Si el texto del comando que especifica el usuario representa un procedimiento en lugar de una vista, el comportamiento es dependerá del proveedor. **Anexar** se producirá un error si el proveedor no admite comandos persistentes.  
  
> [!NOTE]
>  Cuando se utiliza el proveedor OLE DB para Microsoft Jet, el **vistas** colección **anexado** método le permitirá especificar una **procedimiento** en lugar de un **vista**  en el *comando* parámetro. El **procedimiento** se agregará al origen de datos y se agregará a la **vistas** colección. Después de la **anexado**, si la **procedimientos** y **vistas** se actualizan las colecciones, el **procedimiento** ya no estará en el **Vistas** colección y se mostrarán en el **procedimientos** colección.  
  
## <a name="applies-to"></a>Se aplica a  
 [Colección de vistas (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)  
  
## <a name="see-also"></a>Vea también  
 [Vistas de ejemplo de método Append (VB)](../../../ado/reference/adox-api/views-append-method-example-vb.md)   
 [Append (método) (columnas ADOX)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append (método) (grupos ADOX)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append (método) (índices ADOX)](../../../ado/reference/adox-api/append-method-adox-indexes.md)   
 [Append (método) (claves ADOX)](../../../ado/reference/adox-api/append-method-adox-keys.md)   
 [Append (método) (ADOX procedimientos)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [Append (método) (tablas ADOX)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [Append (método) (usuarios ADOX)](../../../ado/reference/adox-api/append-method-adox-users.md)
