---
title: Cmdlet Invoke-ProcessPartition | Documentos de Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: powershell
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 516fab44-734e-425b-9bd0-b4aee1fd338f
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b29970facb251e859e1e845c00d4c12587ca33c4
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="invoke-processpartition-cmdlet"></a>Cmdlet Invoke-ProcessPartition

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Procesar una partición utilizando una variable concreta del tipo de procesamiento.  

>[!NOTE] 
>En este artículo puede contener información no actualizada y ejemplos. Use el cmdlet Get-Help para la versión más reciente.
  
## <a name="syntax"></a>Sintaxis  
 `Invoke-ProcessPartition [-Name] <System.String> [-Database] <System.String> [-ProcessType] <Microsoft.AnalysisServices.ProcessType> [-CubeName] <System.String> [-MeasureGroupName] <System.String> [<CommonParameters>]`  
  
 `Invoke-ProcessPartition –DatabasePartition <Microsoft.AnalysisServices.Partition> [-ProcessType] <Microsoft.AnalysisServices.ProcessType> [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 El cmdlet Invoke-ProcessPartition procesa una partición específica de una base de datos de Analysis Services, un cubo y un grupo de medida proporcionados. El valor de ProcessType determina el ámbito de la operación. Al procesar una partición, debe especificar el tipo de procesamiento. Para obtener más información, vea [Opciones y valores de procesamiento &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md).  
  
## <a name="parameters"></a>Parámetros  
  
### <a name="-name-string"></a>-Nombre \<cadena >  
 Especifica la partición que se va a procesar.  
  
|||  
|-|-|  
|¿Requerido?|true|  
|¿Posición?|0|  
|Valor predeterminado||  
|¿Aceptar la entrada de la canalización?|false|  
|¿Aceptar caracteres comodín?|false|  
  
### <a name="-database-string"></a>-Base de datos \<cadena >  
 Especifica la base de datos a la que el cubo pertenece.  
  
|||  
|-|-|  
|¿Requerido?|true|  
|¿Posición?|1|  
|Valor predeterminado||  
|¿Aceptar la entrada de la canalización?|false|  
|¿Aceptar caracteres comodín?|false|  
  
### <a name="-cubename-string"></a>-CubeName \<cadena >  
 Especifica el cubo al que pertenece el grupo de medida.  
  
|||  
|-|-|  
|¿Requerido?|true|  
|¿Posición?|2|  
|Valor predeterminado||  
|¿Aceptar la entrada de la canalización?|false|  
|¿Aceptar caracteres comodín?|false|  
  
### <a name="-measuregroupname-string"></a>-MeasureGroupName \<cadena >  
 Especifica el grupo de medida al que la partición pertenece.  
  
|||  
|-|-|  
|¿Requerido?|true|  
|¿Posición?|2|  
|Valor predeterminado||  
|¿Aceptar la entrada de la canalización?|false|  
|¿Aceptar caracteres comodín?|false|  
  
### <a name="-databasepartition-microsoftanalysisservicespartition"></a>-DatabasePartition \<Microsoft.AnalysisServices.Partition >  
 Especifica la partición que se va a procesar.  
  
|||  
|-|-|  
|¿Requerido?|true|  
|¿Posición?|2|  
|Valor predeterminado||  
|¿Aceptar la entrada de la canalización?|false|  
|¿Aceptar caracteres comodín?|false|  
  
### <a name="-processtype-microsoftanalysisservicesprocesstype"></a>-ProcessType \<Microsoft.AnalysisServices.ProcessType >  
 Especifica el tipo de proceso: ProcessFull, ProcessAdd, ProcessUpdate, ProcessIndexes, ProcessData, ProcessDefault, ProcessClear, ProcessStructure, ProcessCelarStructureOnly, ProcessScriptCache o ProcessRecalc.  
  
|||  
|-|-|  
|¿Requerido?|true|  
|¿Posición?|con nombre|  
|Valor predeterminado||  
|¿Aceptar la entrada de la canalización?|false|  
|¿Aceptar caracteres comodín?|false|  
  
### <a name="commonparameters"></a>\<CommonParameters >  
 Este cmdlet admite los parámetros comunes: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer y -OutVariable. Para más información, vea [about_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## <a name="inputs-and-outputs"></a>Entradas y salidas  
 El tipo de entrada es el tipo de objetos que se pueden canalizar al cmdlet. El tipo de valor devuelto es el tipo de objeto que el cmdlet devuelve.  
  
|||  
|-|-|  
|Entradas|None|  
|Salidas|None|  
  
## <a name="example-1"></a>Ejemplo 1  
 `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Cubes\Adventure Works\MeasureGroups\Sales Orders\Partitions\Total_Orders_2004 > Get-Item .| Invoke-ProcessPartition –ProcessType:ProcessDefault`  
  
 Este comando canaliza la identidad de la partición que se va a procesar.  
  
## <a name="example-2"></a>Ejemplo 2  
 `PS SQL SERVER:\sqlas\locahost\default\Databases\AWTEST\Cubes\Adventure Works\MeasureGroups> Invoke-ProcessPartition –Name “Total_Orders_2003” –MeasureGroupname “Sales Order” –CubeName “Adventure Works” –database “AWTEST” –ProcessType “ProcessFull”`  
  
 Este comando procesa la partición Total_Orders_2003 en el grupo de medidas Sales Orders de la base de datos AWTEST.  
  
  
  

