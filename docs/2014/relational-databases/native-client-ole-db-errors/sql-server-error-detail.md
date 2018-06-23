---
title: Detalles del Error SQL Server | Documentos de Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], error details
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error details
- ISQLServerErrorInfo interface
ms.assetid: 51500ee3-3d78-47ec-b90f-ebfc55642e06
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cbbf2365603998edabe58a01de840f2969a8c263
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36198675"
---
# <a name="sql-server-error-detail"></a>Detalles de errores de SQL Server
  El [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] proveedor OLE DB de Native Client define la interfaz de error específico del proveedor [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md). La interfaz devuelve más detalles acerca de un error de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y resulta útil cuando se produce un error en la ejecución del comando o en operaciones de conjunto de filas.  
  
 Hay dos maneras de obtener acceso a **ISQLServerErrorInfo** interfaz.  
  
 El consumidor puede llamar a **IErrorRecords:: Getcustomererrorobject** para obtener un **ISQLServerErrorInfo** puntero, como se muestra en el ejemplo de código siguiente. (No es necesario obtener **ISQLErrorInfo.**) Ambos **ISQLErrorInfo** y **ISQLServerErrorInfo** son objetos de error de OLE DB personalizados; **ISQLServerErrorInfo** es la interfaz que se usa para obtener información de errores de servidor, incluidos detalles como el procedimiento nombre y números de línea.  
  
```  
// Get the SQL Server custom error object.  
if(FAILED(hr=pIErrorRecords->GetCustomErrorObject(  
   nRec, IID_ISQLServerErrorInfo,  
   (IUnknown**)&pISQLServerErrorErrorInfo)))  
```  
  
 Otra manera de obtener un **ISQLServerErrorInfo** puntero consiste en llamar a la **QueryInterface** método en una ya obtenido **ISQLErrorInfo** puntero. Tenga en cuenta que, dado que **ISQLServerErrorInfo** contiene un supraconjunto de la información disponible en **ISQLErrorInfo**, tiene sentido para ir directamente a **ISQLServerErrorInfo**a través de **GetCustomerErrorObject**.  
  
 El **ISQLServerErrorInfo** interfaz expone una función miembro, [ISQLServerErrorInfo:: GetErrorInfo](../native-client-ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md). La función devuelve un puntero a una estructura SSERRORINFO y un puntero a un búfer de cadena. Ambos punteros hacen referencia a memoria que el consumidor debe desasignar utilizando el **IMalloc:: Free** método.  
  
 El consumidor interpreta los miembros de la estructura SSERRORINFO de la siguiente manera.  
  
|Miembro|Descripción|  
|------------|-----------------|  
|*pwszMessage*|Mensaje de error de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Idéntica a la cadena devuelta en **IErrorInfo:: GetDescription**.|  
|*pwszServer*|Nombre de la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en la sesión.|  
|*pwszProcedure*|Si procede, nombre del procedimiento donde se ha producido el error. De lo contrario, una cadena vacía.|  
|*lNative*|Número del error nativo de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Idéntico al valor devuelto en el *plNativeError* parámetro de **ISQLErrorInfo:: GetSQLInfo**.|  
|*bState*|Estado de un mensaje de error de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*bClass*|Gravedad de un mensaje de error de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|*wLineNumber*|Si procede, número de línea del procedimiento almacenado donde se produjo el error.|  
  
## <a name="see-also"></a>Vea también  
 [Errores](errors.md)   
 [RAISERROR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
