---
title: SetPermissions (método, ADOX) | Documentos de Microsoft
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
apitype: COM
f1_keywords:
- User25::SetPermissions
- User25::raw_SetPermissions
- _Group25::SetPermissions
- _Group25::raw_SetPermissions
helpviewer_keywords:
- SetPermissions method [ADOX]
ms.assetid: b7f925d7-b05c-4376-bb49-f8d2c17b8b24
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3bcc44011a880f05489be5cc1fcf5e398629d01d
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="setpermissions-method-adox"></a>SetPermissions (método, ADOX)
Especifica los permisos para un [grupo](../../../ado/reference/adox-api/group-object-adox.md) o [usuario](../../../ado/reference/adox-api/user-object-adox.md) en un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
GroupOrUser.SetPermissions Name, ObjectType, Action, Rights [, Inherit] [, ObjectTypeId]  
```  
  
#### <a name="parameters"></a>Parámetros  
 *Nombre*  
 A **cadena** valor que especifica el nombre del objeto para el que se va a establecer permisos.  
  
 *ObjectType*  
 A **largo** valor que puede ser uno de los [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) constantes, que especifica el tipo del objeto para el que se va a obtener permisos.  
  
 *Acción*  
 A **largo** valor que puede ser uno de los [ActionEnum](../../../ado/reference/adox-api/actionenum.md) constantes que especifica el tipo de acción que se realizará cuando se establecen permisos.  
  
 *Derechos*  
 A **largo** valor que puede ser una máscara de bits de uno o varios de los [RightsEnum](../../../ado/reference/adox-api/rightsenum.md) constantes, que indica los derechos a establecer.  
  
 *Heredar*  
 Opcional. A **largo** valor que puede ser uno de los [InheritTypeEnum](../../../ado/reference/adox-api/inherittypeenum.md) constantes, que especifica cómo objetos heredará estos permisos. El valor predeterminado es **adInheritNone**.  
  
 *Valor de ObjectTypeId*  
 Opcional. A **Variant** valor que especifica el GUID de un tipo de objeto de proveedor que no está definido por la especificación de OLE DB. Este parámetro es obligatorio si *ObjectType* está establecido en **adPermObjProviderSpecific**; en caso contrario, no se utiliza.  
  
## <a name="remarks"></a>Comentarios  
 Se producirá un error si el proveedor no admite la configuración de derechos de acceso para grupos o usuarios.  
  
> [!NOTE]
>  Al llamar a **SetPermissions**, la configuración de acciones **adAccessRevoke** reemplaza siempre cualquier configuración de la *derechos* parámetro. No establezca *acciones* a **adAccessRevoke** si desea que los derechos especificados en el *derechos* parámetro surta efecto.  
  
## <a name="applies-to"></a>Se aplica a  
  
|||  
|-|-|  
|[Objeto Group (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[Objeto User (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo GetPermissions y SetPermissions métodos (VB)](../../../ado/reference/adox-api/getpermissions-and-setpermissions-methods-example-vb.md)   
 [GetPermissions (método, ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)   
 [Name (propiedad, ADOX)](../../../ado/reference/adox-api/name-property-adox.md)
