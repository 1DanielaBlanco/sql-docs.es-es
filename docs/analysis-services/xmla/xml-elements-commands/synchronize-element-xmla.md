---
title: Elemento Synchronize (XMLA) | Documentos de Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 87e0751258194828e58e357521a2a10515e1faad
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="synchronize-element-xmla"></a>Elemento Synchronize (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Sincroniza una [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de datos con otra base de datos existente.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Command>  
   <Synchronize>  
      <Source>...</Source>  
      <SynchronizeSecurity>...</SynchronizeSecurity>  
      <ApplyCompression>...</ApplyCompression>  
      <Locations>...</Locations>  
   </Synchronize>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|Ninguno|  
|Valor predeterminado|Ninguno|  
|Cardinalidad|0-n: elemento opcional que puede aparecer más de una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Elementos secundarios|[ApplyCompression](../../../analysis-services/xmla/xml-elements-properties/applycompression-element-xmla.md), [ubicaciones](../../../analysis-services/xmla/xml-elements-properties/locations-element-xmla.md), [origen](../../../analysis-services/xmla/xml-elements-properties/source-element-synchronize-xmla.md), [SynchronizeSecurity](../../../analysis-services/xmla/xml-elements-properties/synchronizesecurity-element-xmla.md)|  
  
## <a name="remarks"></a>Comentarios  
 El comando **Synchronize** sincroniza la base de datos de destino con una instancia de origen y con la base de datos especificadas en el elemento **Source** . Opcionalmente, el comando **Synchronize** sincroniza particiones remotas definidas en la base de datos de origen.  
  
 Dependiendo del modo de almacenamiento utilizado por los objetos guardados en el archivo de copia de seguridad, el comando **Synchronize** sincroniza la información tal y como se indica en la tabla siguiente.  
  
|Modo de almacenamiento|Información|  
|------------------|-----------------|  
|OLAP multidimensional (MOLAP)|Datos de origen, agregaciones y metadatos|  
|OLAP híbrido (HOLAP)|Agregaciones y metadatos|  
|OLAP relacional (ROLAP)|Metadatos|  
  
 Durante la ejecución de un comando **Synchronize** , se establece un bloqueo de lectura en la base de datos de origen y un bloqueo de escritura en la base de datos de destino. Ambos bloqueos se liberan una vez se haya completado la ejecución del comando **Synchronize** .  
  
 Para obtener más información acerca de cómo sincronizar las bases de datos, vea [realizar copias de seguridad, restaurar y sincronizar bases de datos &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Vea también  
 [Elemento backup & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)   
 [Elemento de lote & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)   
 [Elemento Parallel & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md)   
 [Restaurar elemento & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Comandos & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
