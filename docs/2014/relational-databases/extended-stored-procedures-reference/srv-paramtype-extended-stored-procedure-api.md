---
title: srv_paramtype (API de procedimiento almacenado extendido) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- srv_paramtype
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramtype
ms.assetid: badc6d36-8a87-42b5-b28c-9c4f5ded8552
caps.latest.revision: 32
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7ec38d14a34ed7718c9bb58f6fb3802cc98d531c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37294794"
---
# <a name="srvparamtype-extended-stored-procedure-api"></a>srv_paramtype (API de procedimiento almacenado extendido)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Use la integración con CLR en su lugar.  
  
 Devuelve el tipo de datos de un parámetro de llamada a un procedimiento almacenado remoto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
int srv_paramtype (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a>Argumentos  
 *srvproc*  
 Es un puntero a la estructura SRV_PROC, que es el identificador de una conexión de cliente determinada (en este caso, el identificador que recibió la llamada al procedimiento almacenado remoto). La estructura contiene información que la biblioteca de API de procedimiento almacenado extendido usa para administrar la comunicación y los datos entre la aplicación y el cliente.  
  
 *n*  
 Indica el número del parámetro. El primer parámetro es 1.  
  
## <a name="returns"></a>Devuelve  
 En valor de token para el tipo de dato del parámetro. Para más información sobre tipos de datos, vea [Data Types &#40;Extended Stored Procedure API&#41; (Tipos de datos &#40;API de procedimiento almacenado extendido&#41;)](data-types-extended-stored-procedure-api.md). Si no existe ningún parámetro *n* o no hay ningún procedimiento almacenado remoto, devuelve -1.  
  
 Esta función devuelve los valores siguientes, si el parámetro es uno de los tipos de datos de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
|Nuevos tipos de datos|Valor devuelto|  
|--------------------|------------------|  
|`BITN`|SRVBIT|  
|`BIGVARCHAR`|VARCHAR|  
|`BIGCHAR`|CHAR|  
|`BIGBINARY`|BINARY|  
|`BIGVARBINARY`|VARBINARY|  
|`NCHAR`|CHAR|  
|`NVARCHAR`|VARCHAR|  
|`NTEXT`|-1|  
  
## <a name="remarks"></a>Notas  
 Cuando se usan parámetros en una llamada a un procedimiento almacenado remoto, estos pueden pasarse por nombre o por posición (sin nombre). Se produce un error si la llamada al procedimiento almacenado remoto se realiza con algunos parámetros pasados por nombre y otros pasados por posición. Sigue llamándose al controlador SRV_RPC, pero parece como si no hubiera ningún parámetro y **srv_rpcparams** devuelve 0.  
  
> [!IMPORTANT]  
>  Debe revisar minuciosamente el código fuente de los procedimientos almacenados extendidos y debe probar las DLL compiladas antes de instalarlas en el servidor de producción. Para obtener información acerca de la revisión y pruebas de seguridad, vea este [sitio web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Vea también  
 [srv_paraminfo &#40;API de procedimiento almacenado extendido&#41;](srv-paraminfo-extended-stored-procedure-api.md)   
 [srv_rpcparams &#40;API de procedimiento almacenado extendido&#41;](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
