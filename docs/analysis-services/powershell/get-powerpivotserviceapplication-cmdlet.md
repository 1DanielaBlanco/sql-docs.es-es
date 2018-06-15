---
title: Cmdlet Get-PowerPivotServiceApplication | Documentos de Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2a5ccd05b8c5e947972218a22c0abbc358731ee5
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
ms.locfileid: "34027875"
---
# <a name="get-powerpivotserviceapplication-cmdlet"></a>Cmdlet Get-PowerPivotServiceApplication
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Devuelve una o varias aplicaciones de servicio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  

>[!NOTE] 
>En este artículo puede contener información no actualizada y ejemplos. Use el cmdlet Get-Help para la versión más reciente.
  
 **Se aplica a:** SharePoint 2010 y SharePoint 2013.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Get-PowerPivotServiceApplication [[-Identity] <SPGeminiServiceApplicationPipeBind>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 El cmdlet Get-PowerPivotServiceApplication devuelve la aplicación de servicio especificada por el parámetro Identity. Si no se especifica ningún parámetro, el cmdlet devuelve todas las aplicaciones de servicio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] en la granja de servidores. Cada aplicación se identifica mediante su nombre para mostrar, tipo de aplicación y GUID. Para ver propiedades adicionales de una aplicación de servicio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , agregue la opción format-list al cmdlet.  
  
## <a name="parameters"></a>Parámetros  
  
### <a name="-identity-spgeminiserviceapplicationpipebind"></a>-Identity \<SPGeminiServiceApplicationPipeBind >  
 Especifica la aplicación de servicio que se va a obtener. El valor debe ser un GUID válido que identifique de forma única el objeto en la granja.  
  
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
|Resultados|Ninguno.|  
  
## <a name="example-1"></a>Ejemplo 1  
  
```  
C:\PS>Get-PowerPivotServiceApplication  
```  
  
 Este ejemplo devuelve una o varias aplicaciones de servicios de la granja.  
  
## <a name="example-2"></a>Ejemplo 2  
  
```  
C:\PS>Get-PowerPivotServiceApplication | format-list  
```  
  
 Este ejemplo devuelve todas las propiedades de una aplicación de servicio [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
## <a name="example-3"></a>Ejemplo 3  
  
```  
C:\PS>get-PowerPivotServiceApplication -Identity 1234567-890a-bcde-fghijklm  
```  
  
 Este ejemplo devuelve una única aplicación de servicio y muestra el nombre para mostrar, el tipo de aplicación y el GUID de la aplicación. Si el nombre para mostrar es largo, se truncará. Use la opción format-list para ver el nombre completo.  
  
  
