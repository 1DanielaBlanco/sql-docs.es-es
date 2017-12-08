---
title: Cmdlet Get-PowerPivotSystemService | Documentos de Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: powershell
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 33231250-3880-4d75-936b-d70662a01855
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2773e1b0d0331dc1396da5a471549a90f72664d5
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="get-powerpivotsystemservice-cmdlet"></a>Cmdlet Get-PowerPivotSystemService

[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  Devuelve las propiedades globales del objeto Servicio de sistema de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] en una granja. 

>[!NOTE] 
>En este artículo puede contener información no actualizada y ejemplos. Use el cmdlet Get-Help para la versión más reciente.
  
 **Se aplica a:** SharePoint 2010 y SharePoint 2013.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Get-PowerPivotSystemService [-Identity <PowerPivotMidTierServicePipeBind>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 El cmdlet Get-PowerPivotSystemService devuelve las propiedades globales del objeto Servicio de sistema de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . Hay un objeto primario en cada granja, pero cada granja puede tener varias instancias del Servicio de sistema de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] que se ejecutan en servidores de aplicaciones individuales de la granja. El objeto primario muestra los valores del nivel de granja que no cambian según la instancia. Si la granja incluye varias instalaciones de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] para SharePoint, una lista delimitada por comas de las instancias indicará el número de instancias del Servicio de sistema de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] en la granja.  
  
## <a name="parameters"></a>Parámetros  
  
### <a name="-identity-powerpivotmidtierservicepipebind"></a>-Identity \<PowerPivotMidTierServicePipeBind >  
 Especifica el objeto primario que se va a obtener. El valor debe ser un GUID válido que identifique de forma única el objeto en la granja.  
  
|||  
|-|-|  
|¿Requerido?|false|  
|¿Posición?|0|  
|Valor predeterminado||  
|¿Aceptar la entrada de la canalización?|true|  
|¿Aceptar caracteres comodín?|false|  
  
### <a name="commonparameters"></a>\<CommonParameters >  
 Este cmdlet admite parámetros comunes: Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable,OutBuffer y OutVariable. Para obtener más información, vea [about_Commonparameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Entradas y salidas  
 El tipo de entrada es el tipo de objetos que se pueden canalizar al cmdlet. El tipo de valor devuelto es el tipo de objeto que el cmdlet devuelve.  
  
|||  
|-|-|  
|Entradas|Ninguno.|  
|Salidas|Ninguno.|  
  
## <a name="example-1"></a>Ejemplo 1  
  
```  
C:\PS>Get-PowerPivotSystemService  
```  
  
 Este ejemplo devuelve las propiedades globales del objeto primario y muestra las propiedades que pueden compartir todas las instancias del Servicio de sistema de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] en la granja.  
  
  
