---
title: Desarrollar con XMLA en Analysis Services | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- XML for Analysis, data mining
- commands [XML for Analysis]
- data mining [XML for Analysis]
- XMLA, data mining
- XML for Analysis, Analysis Services tasks
- XMLA, Analysis Services tasks
ms.assetid: 54445ee7-720c-4683-99a6-e75b3dcca904
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 04c3459dca4edabcc56753a076bad1e4ffdddfde
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36204051"
---
# <a name="developing-with-xmla-in-analysis-services"></a>Desarrollar con XMLA en Analysis Services
  XML for Analysis (XMLA) es un protocolo XML basado en SOAP, diseñado específicamente para el acceso universal a los datos de cualquier origen de datos multidimensionales estándar a los que se puede acceder mediante una conexión HTTP. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] usa XMLA como único protocolo al comunicar con aplicaciones cliente. Básicamente, todas las bibliotecas de cliente admitidas por Analysis Services formulan solicitudes y respuestas en XMLA.  
  
 Como desarrollador, puede usar XMLA para integrar una aplicación cliente con [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], sin dependencias en las interfaces COM o .NET Framework. Los requisitos de la aplicación que incluyen el hospedaje en una amplia variedad de plataformas se pueden satisfacer utilizando XMLA y una conexión HTTP a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cumple totalmente la especificación 1.1 de XMLA, pero también la extiende para habilitar la definición de datos, la manipulación de datos y el soporte de control de datos. Se hace referencia a las extensiones de Analysis Services como Analysis Services Scripting Language (ASSL). El uso conjunto de XMLA y ASSL habilita un conjunto más amplio de funciones que las proporcionadas por XMLA en solitario. Para obtener más información acerca de ASSL, vea [desarrollar con Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md).  
  
## <a name="in-this-section"></a>En esta sección  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Administrar conexiones y sesiones &#40;XMLA&#41;](managing-connections-and-sessions-xmla.md)|Describe cómo conectar con una instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] y cómo administrar las sesiones y la disponibilidad de estados en XMLA.|  
|[Controlar errores y advertencias &#40;XMLA&#41;](handling-errors-and-warnings-xmla.md)|Describe cómo [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] devuelve información sobre errores y advertencias para los métodos y comandos en XMLA.|  
|[Definir e identificar objetos &#40;XMLA&#41;](../xmla/xml-elements-objects.md)|Describe identificadores de objetos y referencias a objetos y cómo usar identificadores y referencias dentro de los comandos XMLA.|  
|[Administrar transacciones &#40;XMLA&#41;](managing-transactions-xmla.md)|Detalla cómo utilizar el [BeginTransaction](../xmla/xml-elements-commands/begintransaction-element-xmla.md), [CommitTransaction](../xmla/xml-elements-commands/committransaction-element-xmla.md), y [RollbackTransaction](../xmla/xml-elements-commands/rollbacktransaction-element-xmla.md) comandos para definir y administrar una transacción en el XMLA actual explícitamente sesión.|  
|[Cancelar comandos &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/canceling-commands-xmla.md)|Describe cómo utilizar el [cancelar](../xmla/xml-elements-commands/cancel-element-xmla.md)comando para cancelar comandos, sesiones y conexiones en XMLA.|  
|[Realizar operaciones por lotes &#40;XMLA&#41;](performing-batch-operations-xmla.md)|Describe cómo utilizar el [lote](../xmla/xml-elements-commands/batch-element-xmla.md) comando para ejecutar XMLA varios comandos, en serie o en paralelo, ya sea en la misma transacción o como transacciones independientes, con un único XMLA [Execute](../xmla/xml-elements-methods-execute.md) método.|  
|[Crear y modificar objetos &#40;XMLA&#41;](creating-and-altering-objects-xmla.md)|Describe cómo utilizar el [crear](../xmla/xml-elements-commands/create-element-xmla.md), [Alter](../xmla/xml-elements-commands/alter-element-xmla.md), y [eliminar](../xmla/xml-elements-commands/delete-element-xmla.md) comandos, junto con elementos de Analysis Services Scripting Language (ASSL), para definir, cambiar o quitar objetos de un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instancia.|  
|[Bloqueo y desbloqueo de las bases de datos &#40;XMLA&#41;](locking-and-unlocking-databases-xmla.md)|Detalla cómo utilizar el [bloqueo](../xmla/xml-elements-commands/lock-element-xmla.md) y [Unlock](../xmla/xml-elements-commands/unlock-element-xmla.md) comandos para bloquear y desbloquear un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de datos.|  
|[Procesar objetos &#40;XMLA&#41;](processing-objects-xmla.md)|Describe cómo utilizar el [proceso](../xmla/xml-elements-commands/process-element-xmla.md) comando al proceso una [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objeto.|  
|[Mezclar particiones &#40;XMLA&#41;](merging-partitions-xmla.md)|Describe cómo utilizar el [MergePartitions](../xmla/xml-elements-commands/mergepartitions-element-xmla.md) comando mezclar particiones en un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instancia.|  
|[Diseñar agregaciones &#40;XMLA&#41;](designing-aggregations-xmla.md)|Describe cómo utilizar el [DesignAggregations](../xmla/xml-elements-commands/designaggregations-element-xmla.md) comando, ya sea en iterativo o en modo por lotes, para diseñar agregaciones para un diseño de agregaciones en [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|[Copia de seguridad, restaurar y sincronizar las bases de datos &#40;XMLA&#41;](backing-up-restoring-and-synchronizing-databases-xmla.md)|Describe cómo utilizar el [copia de seguridad](../xmla/xml-elements-commands/backup-element-xmla.md) y [restaurar](../xmla/xml-elements-commands/restore-element-xmla.md) comandos para copia de seguridad y restaurar un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de datos desde un archivo de copia de seguridad.<br /><br /> También describe cómo utilizar el [sincronizar](../xmla/xml-elements-commands/synchronize-element-xmla.md) comando para sincronizar un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] base de datos con una base de datos existente en la misma instancia o en una instancia diferente.|  
|[Insertar, actualizar y quitar miembros &#40;XMLA&#41;](inserting-updating-and-dropping-members-xmla.md)|Describe cómo utilizar el [insertar](../xmla/xml-elements-commands/insert-element-xmla.md), [actualización](../xmla/xml-elements-commands/update-element-xmla.md), y [Drop](../xmla/xml-elements-commands/drop-element-xmla.md) comandos para agregar, cambiar o eliminar miembros de una dimensión habilitada para escritura.|  
|[Actualizar celdas &#40;XMLA&#41;](updating-cells-xmla.md)|Describe cómo utilizar el [UpdateCells](../xmla/xml-elements-commands/updatecells-element-xmla.md) comando para cambiar los valores de las celdas de una partición habilitada para escritura.|  
|[Administración de cachés &#40;XMLA&#41;](managing-caches-xmla.md)|Detalla cómo utilizar el [ClearCache](../xmla/xml-elements-commands/clearcache-element-xmla.md) comando para borrar las cachés de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objetos.|  
|[Supervisar los seguimientos &#40;XMLA&#41;](monitoring-traces-xmla.md)|Describe cómo utilizar el [suscribir](../xmla/xml-elements-commands/subscribe-element-xmla.md) comando para suscribirse a y supervisar un seguimiento existente en un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instancia.|  
  
## <a name="data-mining-with-xmla"></a>Minería de datos con XMLA  
 XML for Analysis es totalmente compatible con los conjuntos de filas de esquema de minería de datos. Estos conjuntos de filas proporcionan información para consultar modelos de minería de datos utilizando la [Discover](../xmla/xml-elements-methods-discover.md) método. Para obtener más información acerca de conjuntos de filas de esquema de minería de datos, vea [conjuntos de filas de esquema de minería de datos](../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
 Para obtener más información acerca de DMX, vea [extensiones de minería de datos &#40;DMX&#41; referencia](/sql/dmx/data-mining-extensions-dmx-reference).  
  
## <a name="namespace-and-schema"></a>Espacio de nombres y esquema  
  
### <a name="namespace"></a>Espacio de nombres  
 El esquema definido en esta especificación utiliza el espacio de nombres XML http://schemas.microsoft.com/AnalysisServices/2003/Engine y la abreviatura estándar "DDL".  
  
### <a name="schema"></a>esquema  
 La definición de un esquema de lenguaje de definición de esquema XML (XSD) para el lenguaje de definición de objeto de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] se basa en la definición de la jerarquía y los elementos del esquema en esta sección.  
  
## <a name="extensibility"></a>Extensibilidad  
 La extensibilidad del esquema de lenguaje de definición de objeto se proporciona por medio de un elemento `Annotation` que se incluye en todos los objetos. Este elemento puede contener XML válido de cualquier espacio de nombres XML (excepto el espacio de nombres de destino que define el DDL), sujeto a las reglas siguientes:  
  
-   El XML solo puede contener elementos.  
  
-   Cada elemento debe tener un nombre único. Se recomienda que el valor de `Name` haga referencia al espacio de nombres de destino.  
  
 Estas reglas se imponen para que el contenido de la etiqueta `Annotation` pueda exponerse como un conjunto de pares nombre/valor a través de la versión 9.0 de DSO (Objetos de ayuda para la toma de decisiones).  
  
 No se pueden conservar los comentarios y los espacios en blanco dentro de la etiqueta `Annotation` que no se incluyen dentro de un elemento secundario. Además, todos los elementos deben ser de lectura y escritura; los elementos de solo lectura se omiten.  
  
 El esquema de lenguaje de definición de objeto es de tipo cerrado; el servidor no permite la sustitución de tipos derivados de los elementos definidos en el esquema. Por lo tanto, el servidor solamente acepta el conjunto de elementos aquí definidos y ningún otro elemento o atributo. Los elementos desconocidos hacen que el motor de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] genere un error.  
  
## <a name="see-also"></a>Vea también  
 [Desarrollar aplicaciones con Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Descripción de la arquitectura OLAP de Microsoft](../multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  
