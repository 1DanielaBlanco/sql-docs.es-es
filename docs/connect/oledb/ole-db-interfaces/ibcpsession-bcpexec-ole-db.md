---
title: Ibcpsession (OLE DB) | Documentos de Microsoft
description: IBCPSession::BCPExec (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IBCPSession::BCPExec (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPExec method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: f7605b7ffd804ca3c90ecb98bf4e77312fd8902a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="ibcpsessionbcpexec-ole-db"></a>IBCPSession::BCPExec (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Realiza la operación de copia masiva.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
HRESULT BCPExec(   
      DBROWCOUNT *pRowsCopied);  
```  
  
## <a name="remarks"></a>Comentarios  
 El **BCPExec** método copia los datos de un archivo de usuario a una tabla de base de datos o viceversa, dependiendo del valor de la *eDirection* parámetro utilizado con el [ibcpsession:: BCPInit](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)(método).  
  
 Antes de llamar a **BCPExec**, llame al método **BCPInit** con un nombre de archivo de usuario válido. Si no lo hace, se producirá un error. La única excepción es que una consulta vaya a utilizarse para una operación de salida de copia masiva. En ese caso, especifique NULL para el nombre de tabla en el método **BCPInit** y, a continuación, especifique la consulta mediante la opción BCP_OPTION_HINTS.  
  
 El método **BCPExec** es el único método de copia masiva que es probable que quede pendiente durante un período de tiempo indeterminado. Por lo tanto, es el único método de copia masiva que admite el modo asincrónico. Para usar el modo asincrónico, establezca la propiedad de sesión SSPROP_ASYNCH_BULKCOPY específica del proveedor en VARIANT_TRUE antes de llamar al método **BCPExec** . Esta propiedad se encuentra disponible en el conjunto de propiedades DBPROPSET_SQLSERVERSESSION. Para comprobar si se ha completado, llame al método **BCPExec** con los mismos parámetros. Si la copia masiva aún no se ha completado, el método **BCPExec** devuelve DB_S_ASYNCHRONOUS. También devuelve en el argumento *pRowsCopied* un recuento de estado del número de filas que se han enviado al servidor o que se han recibido del servidor. Las filas enviadas al servidor no se confirman hasta que se alcanza el final de un lote.  
  
## <a name="arguments"></a>Argumentos  
 *pRowsCopied*[out]  
 Puntero a un valor de tipo DWORD. El método **BCPExec** rellena el valor DWORD con el número de filas que se han copiado correctamente. Si el argumento *pRowsCopied* está establecido en NULL, el método **BCPExec** lo omite.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 S_OK  
 El método se ha llevado a cabo de forma correcta.  
  
 E_FAIL  
 Se produjo un error específico del proveedor; Para obtener información detallada, use la [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) interfaz.  
  
 E_UNEXPECTED  
 No se esperaba la llamada al método. Por ejemplo, no se llamó al método **BCPInit** antes de llamar a este método. También se produce si la operación se anuló mediante el uso de la opción BCP_OPTION_ABORT y después se llamó al método **BCPExec** .  
  
 E_OUTOFMEMORY  
 Error de memoria insuficiente.  
  
 DB_S_ENDOFROWSET  
 La operación de copia masiva finalizó y se completó toda la operación de transferencia de datos.  
  
 DB_S_ASYNCHRONOUS  
 Se copió el lote actual de filas. Vuelva a llamar al método **BCPExec** para transferir el siguiente lote.  
  
 DB_S_ERRORSOCCURRED  
 Se produjeron errores durante la operación de copia masiva y algunas filas no pudieron copiarse. El número de errores sigue siendo menor al número máximo de errores permitidos.  
  
## <a name="see-also"></a>Vea también  
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [Realizar operaciones de copia masiva](../../oledb/features/performing-bulk-copy-operations.md)  
  
  
