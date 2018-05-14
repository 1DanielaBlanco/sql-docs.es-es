---
title: Cmdlet Remove-PowerPivotServiceApplication | Documentos de Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 30b7826bf0239ed59b0b94ce624ab1eb212a34fc
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="remove-powerpivotserviceapplication-cmdlet"></a>Cmdlet Remove-PowerPivotServiceApplication
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Elimina una aplicación de servicio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  

>[!NOTE] 
>En este artículo puede contener información no actualizada y ejemplos. Use el cmdlet Get-Help para la versión más reciente.
  
 **Se aplica a:** SharePoint 2010 y SharePoint 2013.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Remove-PowerPivotServiceApplication [-Identity <SPGeminiServiceApplicationPipeBind>] [-DeleteAll <switch>] [-RemoveData <switch>] [-Confirm <switch>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 El cmdlet Remove-PowerPivotServiceApplication elimina una aplicación de servicio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] de la granja. Use DeleteAll para eliminar todas las aplicaciones de servicio a la vez o use el parámetro Identitiy para quitar una sola instancia. Para obtener información de la instancia, ejecute Get-PowerPivotServiceApplication para devolver todas las instancias de la granja.  
  
 Use el parámetro RemoveData para quitar si lo desea las bases de datos de aplicación de servicio y los archivos almacenados en memoria caché. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] permanecen en bibliotecas de contenido, pero ya no son funcionales una vez que se quita la aplicación de servicio.  
  
## <a name="parameters"></a>Parámetros  
  
### <a name="-identity-spgeminiserviceapplicationpipebind"></a>-Identity \<SPGeminiServiceApplicationPipeBind >  
 Especifica el GUID de una aplicación de servicio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] en la granja. Debe especificar el GUID si desea quitar simplemente una aplicación, dejando intactas otras aplicaciones de servicios.  
  
|||  
|-|-|  
|¿Requerido?|false|  
|¿Posición?|0|  
|Valor predeterminado||  
|¿Aceptar la entrada de la canalización?|true|  
|¿Aceptar caracteres comodín?|false|  
  
### <a name="-confirm-switch"></a>-Confirme \<cambiar >  
 Le solicita confirmación antes de ejecutar el comando. Este valor se habilita de forma predeterminada. Para omitir la respuesta de confirmación de un comando, especifique Confirm:$false en el comando.  
  
|||  
|-|-|  
|¿Requerido?|false|  
|¿Posición?|con nombre|  
|Valor predeterminado||  
|¿Aceptar la entrada de la canalización?|false|  
|¿Aceptar caracteres comodín?|false|  
  
### <a name="-deleteall-switch"></a>-DeleteAll \<cambiar >  
 Elimina todas las aplicaciones de servicio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , pero no elimina la base de datos de aplicación de servicio, ni los objetos de instancia de servicio de la granja. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] y Servicio de motor de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] siguen teniendo instancias después de quitar las aplicaciones de servicio, pero no inservibles.  
  
|||  
|-|-|  
|¿Requerido?|false|  
|¿Posición?|con nombre|  
|Valor predeterminado||  
|¿Aceptar la entrada de la canalización?|false|  
|¿Aceptar caracteres comodín?|false|  
  
### <a name="-removedata-switch"></a>-RemoveData \<cambiar >  
 Quita la base de datos de la aplicación de servicio que contiene las programaciones de las actualizaciones de datos, los datos de uso de libros, los mapas de instancias que se utilizan para realizar el seguimiento de las bases de datos que se cargan y otros datos internos.  
  
|||  
|-|-|  
|¿Requerido?|false|  
|¿Posición?|con nombre|  
|Valor predeterminado||  
|¿Aceptar la entrada de la canalización?|false|  
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
C:\PS>Remove-PowerPivotServiceApplication -identity 12345678-90ab-cdef-ghijklmnop  
```  
  
 En este ejemplo se elimina una única aplicación de servicio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , pero no se quita su base de datos o la caché. Si no especifica una identidad, se le solicitará que proporcione una.  
  
## <a name="example-2"></a>Ejemplo 2  
  
```  
C:\PS>Remove-PowerPivotServiceApplication -DeleteAll  
```  
  
 En este ejemplo se eliminan todas las aplicaciones de servicio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] de la granja. Las bases de datos y la memoria caché no se eliminan.  
  
## <a name="example-3"></a>Ejemplo 3  
  
```  
CC:\PS>Remove-PowerPivotServiceApplication -identity 12345678-90ab-cdef-ghijklmnop -RemoveData  
```  
  
 En este ejemplo se elimina una sola aplicación de servicio de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , junto con sus archivos de base de datos y caché.  
  
  
