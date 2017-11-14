---
title: Registra los objetos de negocios en el cliente para su uso con DCOM | Documentos de Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business objects in RDS [ADO]
ms.assetid: 75a21910-607f-463a-ae18-a17130dafb7e
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e293eb58053259dd229656152094763ac31b48a2
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="registering-business-objects-on-the-client-for-use-with-dcom"></a>Registra los objetos de negocios en el cliente para su uso con DCOM
Objetos comerciales personalizados deben asegurarse de que el cliente puede asignar su nombre de programa (ProgId) con un identificador (CLSID) que se puede usar a través de DCOM. Por este motivo, el ProgID del objeto DCOM debe estar en el registro de cliente y se asignan a lo Id. de clase del objeto comercial de servidor. Para los demás protocolos admitidos (HTTP, HTTPS y en proceso), esto no es necesario.  
  
> [!IMPORTANT]
>  A partir de Windows 8 y Windows Server 2012, componentes de servidor RDS ya no están incluidos en el sistema operativo Windows (consulte Windows 8 y [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) para obtener más detalles). Componentes de cliente RDS se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y tenga previsto modificar las aplicaciones que actualmente la utilizan. Las aplicaciones que utilizan RDS deben migrar a [servicio de datos de WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Por ejemplo, si expone un objeto de negocio de servidor llamado MyBObj, con un identificador de clase específicos, por ejemplo, "{00112233-4455-6677-8899-00AABBCCDDEE}", asegúrese de que se agregan las siguientes entradas en el registro de cliente:  
  
```  
[HKEY_CLASSES_ROOT]  
\MyBObj\Clsid\(Default) "{00112233-4455-6677-8899-00AABBCCDDEE}"  
```



