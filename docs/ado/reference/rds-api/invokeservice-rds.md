---
title: InvokeService (RDS) | Documentos de Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords:
- InvokeService [RDS]
ms.assetid: ad45c676-ec7e-4a3a-9a6b-a54f75eb3012
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0b0cf05dcc458245d1c8d64bd0f5c8d00178db9e
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="invokeservice-rds"></a>InvokeService (RDS)
Devuelve un puntero a la interfaz solicitada en una versión mayor capacidad del objeto.  
  
> [!IMPORTANT]
>  A partir de Windows 8 y Windows Server 2012, componentes de servidor RDS ya no están incluidos en el sistema operativo Windows (consulte Windows 8 y [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) para obtener más detalles). Componentes de cliente RDS se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y tenga previsto modificar las aplicaciones que actualmente la utilizan. Las aplicaciones que utilizan RDS deben migrar a [servicio de datos de WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
object.InvokeService(REFID riid, IUknown* punkNotSoFunctionalInterface, IUknown** ppunkMoreFunctionalInterface) As HRESULT  
```  
  
#### <a name="parameters"></a>Parámetros  
 *riid*  
  
 [in] El identificador de la interfaz que se solicita.  
  
 *punkNotSoFunctionalInterface*  
  
 [in] El objeto de origen con menor capacidad.  
  
 *ppunkMoreFunctionalInterface*  
  
 [out] La dirección de la variable de puntero que recibe el puntero de interfaz solicitado en *riid*. Tras la devolución es correcta, el *ppunkMoreFunctionalInterface* parámetro contiene el puntero de interfaz solicitada para el objeto. Si el objeto no admite la interfaz especificada en *riid*, *ppunkMoreFunctionalInterface* se establece en NULL.  
  
## <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT que indica si la llamada a la **InvokeService** método tuvo éxito.  
  
## <a name="remarks"></a>Comentarios  
 La implementación del motor de cursor RDS de **InvokeService** toma el conjunto de filas de entrada (o un objeto de resultados múltiples), rellena el motor de cursor del conjunto de filas de entrada y, a continuación, devuelve un puntero en sí mismo.  
  
## <a name="applies-to"></a>Se aplica a  
 [Interfaz IRDSService (RDS)](../../../ado/reference/rds-api/irdsservice-interface-rds.md)  
  
## <a name="see-also"></a>Vea también  
 [Métodos RDS](../../../ado/reference/rds-api/rds-methods.md)


