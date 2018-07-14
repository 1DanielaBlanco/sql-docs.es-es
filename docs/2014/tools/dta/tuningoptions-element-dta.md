---
title: TuningOptions (DTA, elemento) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TuningOptions element
ms.assetid: 58a22ba1-8e03-411f-bd46-85e4540f217a
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 30447544b7c2fbfa9bfbe5e8a992605af65da5ca
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261831"
---
# <a name="tuningoptions-element-dta"></a>TuningOptions (DTA, elemento)
  Contiene las opciones de optimización de una sesión de optimización concreta.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions>  
```  
  
## <a name="element-characteristics"></a>Características del elemento  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|**Tipo y longitud de los datos**|Ninguno.|  
|**Valor predeterminado**|Ninguno.|  
|**Repetición**|Opcional. Si usa, sólo puede utilizarse una vez para cada `DTAInput` elemento.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elementos|  
|------------------|--------------|  
|**Elemento primario**|[Elemento DTAInput &#40;DTA&#41;](dtainput-element-dta.md)|  
|**Elementos secundarios**|`ReportSet` elemento. Para obtener más información, vea el [esquema XML del Asistente para la optimización de motor de base de datos](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `TuningLogTable` elemento. Para obtener más información, vea el [esquema XML del Asistente para la optimización de motor de base de datos](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `NumberOfEvents` elemento. Para obtener más información, vea el [esquema XML del Asistente para la optimización de motor de base de datos](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> [TuningTimeInMin, elemento &#40;DTA&#41;](tuningtimeinmin-element-dta.md)<br /><br /> [StorageBoundInMB, elemento &#40;DTA&#41;](storageboundinmb-element-dta.md)<br /><br /> `MaxKeyColumnsInIndex` elemento. Para obtener más información, vea el [esquema XML del Asistente para la optimización de motor de base de datos](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `MaxColumnsInIndex` elemento. Para obtener más información, vea el [esquema XML del Asistente para la optimización de motor de base de datos](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `MinPercentageImprovement` elemento. Para obtener más información, vea el [esquema XML del Asistente para la optimización de motor de base de datos](http://go.microsoft.com/fwlink/?linkid=43100)<br /><br /> [TestServer, elemento &#40;DTA&#41;](server-element-dta.md)<br /><br /> [FeatureSet, elemento &#40;DTA&#41;](featureset-element-dta.md)<br /><br /> [Creación de particiones elemento &#40;DTA&#41;](partitioning-element-dta.md)<br /><br /> [DropOnlyMode, elemento &#40;DTA&#41;](droponlymode-element-dta.md)<br /><br /> [KeepExisting, elemento &#40;DTA&#41;](keepexisting-element-dta.md)<br /><br /> [OnlineIndexOperation, elemento &#40;DTA&#41;](onlineindexoperation-element-dta.md)<br /><br /> [DatabaseToConnect, elemento &#40;DTA&#41;](databasetoconnect-element-dta.md)<br /><br /> `IgnoreConstantsInWorkload` elemento. Para obtener más información, vea el [esquema XML del Asistente para la optimización de motor de base de datos](http://go.microsoft.com/fwlink/?linkid=43100).<br /><br /> `RetainShellDB` elemento. Para obtener más información, vea el [esquema XML del Asistente para la optimización de motor de base de datos](http://go.microsoft.com/fwlink/?linkid=43100).|  
  
## <a name="example"></a>Ejemplo  
 Para obtener ejemplos de la `TuningOptions` elemento, vea el [ejemplos de archivos de entrada XML &#40;DTA&#41;](xml-input-file-samples-dta.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia del archivo de entrada XML &#40;Asistente para la optimización de motor de base de datos&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
