---
title: srv_rpcowner (API de procedimiento almacenado extendido) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- srv_rpcowner
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcowner
ms.assetid: e81a60e6-14ea-47bc-a11c-3d7635344447
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 64ee7f8ad02c141a35cb3bc1cd2f5a599a229f4c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47696293"
---
# <a name="srvrpcowner-extended-stored-procedure-api"></a>srv_rpcowner (API de procedimiento almacenado extendido)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Use la integración con CLR en su lugar.  
  
 Devuelve el componente de propietario del procedimiento almacenado remoto actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
DBCHAR * srv_rpcowner (  
SRV_PROC *  
srvproc  
,  
int *  
len   
);  
```  
  
## <a name="arguments"></a>Argumentos  
 *srvproc*  
 Es un puntero a la estructura SRV_PROC, que es el identificador de una conexión de cliente determinada (en este caso, el identificador que recibió el procedimiento almacenado remoto). La estructura contiene información que la biblioteca de API Procedimiento almacenado extendido utiliza para administrar la comunicación y los datos entre la aplicación y el cliente.  
  
 *len*  
 Es un puntero a una variable entera que recibe la longitud del nombre del propietario. El parámetro *len* puede ser NULL, en cuyo caso no se devuelve la longitud del componente de propietario.  
  
## <a name="returns"></a>Devuelve  
 Un puntero DBCHAR al componente de propietario terminado en NULL para el procedimiento almacenado remoto actual. Si no hay ningún procedimiento almacenado remoto actual, se devuelve NULL y *len* se establece en -1.  
  
## <a name="remarks"></a>Notas  
 Esta función únicamente devuelve el componente de propietario del procedimiento almacenado remoto. No incluye los especificadores opcionales para el nombre, nombre de procedimiento almacenado remoto, y número de procedimiento almacenado remoto.  
  
> [!IMPORTANT]  
>  Debe revisar minuciosamente el código fuente de los procedimientos almacenados extendidos y debe probar las DLL compiladas antes de instalarlas en el servidor de producción. Para obtener información acerca de la revisión y pruebas de seguridad, vea este [sitio web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
