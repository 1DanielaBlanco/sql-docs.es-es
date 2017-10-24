---
title: KEY_GUID (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Key_GUID_TSQL
- Key_GUID
dev_langs:
- TSQL
helpviewer_keywords:
- symmetric keys [SQL Server], GUIDs
- KEY_GUID function
- GUIDs [SQL Server]
ms.assetid: 9246c7b2-7098-42c4-a222-cbf30267c46a
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3e167366e86cf10403abc6cafa894ad964c60733
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="keyguid-transact-sql"></a>KEY_GUID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Devuelve el GUID de una clave simétrica de la base de datos.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Key_GUID( 'Key_Name' )  
```  
  
## <a name="arguments"></a>Argumentos  
 **'** *Key_Name* **'**  
 El nombre de una clave simétrica en la base de datos.  
  
## <a name="return-types"></a>Tipos devueltos  
 **uniqueidentifier**  
  
## <a name="remarks"></a>Comentarios  
 Si se ha especificado un valor de identidad al crear la clave, su GUID es un hash MD5 de ese valor de identidad. Si no se ha especificado ningún valor de identidad, el GUID es generado por el servidor.  
  
 Si la clave es temporal, su nombre debe comenzar con un signo de número (#).  
  
## <a name="permissions"></a>Permissions  
 No se requieren permisos para el acceso a las claves temporales, dado que éstas solo están disponibles en la sesión en la que se crean. Para obtener acceso a una clave que no es temporal, el autor de la llamada necesita algún permiso en ella. Además no puede tener denegado el permiso VIEW en esa clave.  
  
## <a name="examples"></a>Ejemplos  
 En el siguiente ejemplo se devuelve el GUID de una clave simétrica denominada `ABerglundKey1`.  
  
```  
SELECT Key_GUID('ABerglundKey1');  
```  
  
## <a name="see-also"></a>Vea también  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Sys.symmetric_keys &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)   
 [Sys.key_encryptions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-key-encryptions-transact-sql.md)  
  
  

