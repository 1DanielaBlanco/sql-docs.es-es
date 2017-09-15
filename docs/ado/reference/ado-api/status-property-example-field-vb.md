---
title: Ejemplo de la propiedad de estado (campo) (VB) | Documentos de Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Status property [ADO Field], Visual Basic example
ms.assetid: fdd09b60-39c7-44be-8008-e891a031f80e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 91c3418fea062661ffba94feb791d700301ff097
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="status-property-example-field-vb"></a>Ejemplo de la propiedad de estado (campo) (VB)
En el ejemplo siguiente se abre un documento desde una carpeta de lectura/escritura mediante el [Internet Publishing Provider](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). El [estado](../../../ado/reference/ado-api/status-property-ado-field.md) propiedad de un [campo](../../../ado/reference/ado-api/field-object.md) objeto de la [registro](../../../ado/reference/ado-api/record-object-ado.md) primero se establecerá en **adFieldPendingInsert**, a continuación, puede actualizar a **adFieldOk**.  
  
```  
'BeginStatusFieldVB  
  
 ' to integrate this code replace the values in the source string  
  
Sub Main()  
  
   Dim File As ADODB.Record  
   Dim strFile As String  
   Dim Cnxn As ADODB.Connection  
   Dim strCnxn As String  
  
   Set Cnxn = New ADODB.Connection  
   strCnxn = "url=http://MyServer/"  
   Cnxn.Open strCnxn  
  
   Set File = New ADODB.Record  
   strFile = "Folder/FileName"  
   ' Open a read/write document  
   File.Source = strFile  
   File.ActiveConnection = Cnxn  
   File.Mode = adModeReadWrite  
   File.Open  
  
   Debug.Print "Append a couple of fields"  
  
   File.Fields.Append "chektest:fld1", adWChar, 42, adFldUpdatable, "fld1"  
   File.Fields.Append "chektest:fld2", adWChar, 42, adFldUpdatable, "fld2"  
  
   Debug.Print "status for the fields"  
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert  
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert  
  
    'turn off error-handling to verify field status  
   On Error Resume Next  
  
   File.Fields.Update  
  
   Debug.Print "Update succeeds"  
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert + adFieldUnavailable  
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert + adFieldUnavailable  
  
    ' resume default error-handling  
   On Error GoTo 0  
  
     ' clean up  
    File.Close  
    Cnxn.Close  
    Set File = Nothing  
    Set Cnxn = Nothing  
  
End Sub  
'EndStatusFieldVB  
```  
  
 En el ejemplo siguiente se elimina un conocido **campo** desde una **registro** abierto desde un documento. El **estado** propiedad se establecerá en primer lugar **adFieldOK**, a continuación, **adFieldPendingUnknown**.  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
 El siguiente código elimina una **campo** desde una **registro** abierto en un documento de solo lectura. **Estado** se establecerá en **adFieldPendingDelete**. En [actualización](../../../ado/reference/ado-api/update-method.md), se producirá un error en la eliminación y **estado** será **adFieldPendingDelete** más **adFieldPermissionDenied**. [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) borra la pendiente **estado** configuración.  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
## <a name="see-also"></a>Vea también  
 [Objeto Field](../../../ado/reference/ado-api/field-object.md)   
 [Objeto de registro (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Propiedad Status (Field ADO)](../../../ado/reference/ado-api/status-property-ado-field.md)
