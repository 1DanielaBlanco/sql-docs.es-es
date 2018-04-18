---
title: Propiedad PropertyIdx (clase ClientNetworkProtocolProperty) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: wmi
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- PropertyIdx Property (ClientNetworkProtocolProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- PropertyIdx property
ms.assetid: d7845962-ac68-4435-9c59-70ec450fec88
caps.latest.revision: 29
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 52e612599395d2c46ef31bb2e2276bd69227ce8c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="propertyidx-property-clientnetworkprotocolproperty-class"></a>Propiedad PropertyIdx (clase ClientNetworkProtocolProperty)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Obtiene o establece el valor de índice de la propiedad de la matriz de propiedad al que hace referencia el [propiedad Properties (clase ClientNetworkProtocol)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/properties-property-clientnetworkprotocol-class.md) de la [clase ClientNetworkProtocol](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
object.PropertyIdx [= value]  
```  
  
## <a name="parts"></a>Partes  
 *objeto*  
 A [clase ClientNetworkProtocolProperty](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) objeto que representa un atributo de protocolo de red utilizado por el [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cliente.  
  
## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 A **uint32** valor que especifica el valor de índice de matriz de la propiedad actual.  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Configurar protocolos de cliente](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
