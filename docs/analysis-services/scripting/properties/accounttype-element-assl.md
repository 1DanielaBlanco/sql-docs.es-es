---
title: Elemento AccountType (ASSL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- AccountType Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AccountType
helpviewer_keywords:
- AccountType element
ms.assetid: 4fdf17d3-cd84-4bf6-9baf-21e15d4bf71e
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: cdb339861e5b12a9f020af51fe96847fe8ca9b36
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="accounttype-element-assl"></a>Elemento AccountType (ASSL)
  Contiene el nombre de un tipo de cuenta definido en un [base de datos](../../../analysis-services/scripting/objects/database-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Account>  
   ...  
   <AccountType>...</AccountType>  
   ...  
</Account>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|String (enumeración)|  
|Valor predeterminado|Ninguno|  
|Cardinalidad|1-1: Elemento necesario que se produce una vez y solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[Cuenta](../../../analysis-services/scripting/objects/account-element-assl.md)|  
|Elementos secundarios|Ninguno|  
  
## <a name="remarks"></a>Comentarios  
 El valor de este elemento se limita a una de las cadenas enumeradas en la tabla siguiente.  
  
|Valor|Description|  
|-----------|-----------------|  
|*Ingresos*|Es una cuenta de ingresos.|  
|*Gastos*|Es una cuenta de gastos.|  
|*Flujo*|Es una cuenta de flujo de caja.|  
|*Saldo*|Es una cuenta de saldo.|  
|*Activo*|Es una cuenta de activos.|  
|*Responsabilidad*|Es una cuenta de pasivo.|  
|*Estadística*|Es una cuenta de estadística.|  
  
 La enumeración que corresponde a los valores permitidos para **AccountType** en el objeto de Analysis Management Objects (AMO) es el modelo <xref:Microsoft.AnalysisServices.AccountTypes>.  
  
## <a name="see-also"></a>Vea también  
 [Accounts, elemento &#40; ASSL &#41;](../../../analysis-services/scripting/collections/accounts-element-assl.md)   
 [Propiedades &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

