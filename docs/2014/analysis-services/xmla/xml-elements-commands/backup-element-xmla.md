---
title: Copia de seguridad de elemento (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Backup Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Backup
- http://schemas.microsoft.com/analysisservices/2003/engine#Backup
- microsoft.xml.analysis.backup
helpviewer_keywords:
- Backup command
ms.assetid: 5bcbc14c-9db9-45b2-99de-f3a265bcb0c4
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a571681f52fb34e55df238229f659aa883bc84ac
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37215655"
---
# <a name="backup-element-xmla"></a>Elemento Backup (XMLA)
  Realiza copias de seguridad un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de datos a un archivo de copia de seguridad.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Command>  
   <Backup>  
      <Object>...</Object>  
      <File>...</File>  
      <Security>...</Security>  
      <ApplyCompression>...</ApplyCompression>  
      <AllowOverwrite>...</AllowOverwrite>  
      <Password>...</Password>  
      <BackupRemotePartitions>...</BackupRemotePartitions>  
      <Locations>...</Locations>  
   </Backup>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Características del elemento  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|None|  
|Valor predeterminado|None|  
|Cardinalidad|0-n: elemento opcional que puede aparecer más de una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Elementos secundarios|[AllowOverwrite](../xml-elements-properties/allowoverwrite-element-xmla.md), [ApplyCompression](../xml-elements-properties/applycompression-element-xmla.md), [BackupRemotePartitions](../xml-elements-properties/backupremotepartitions-element-xmla.md), [archivo](../xml-elements-properties/file-element-xmla.md), [ubicaciones](../xml-elements-properties/locations-element-xmla.md), [ Objeto](../xml-elements-properties/object-element-xmla.md), [contraseña](../xml-elements-properties/password-element-xmla.md), [seguridad](../xml-elements-properties/security-element-xmla.md)|  
  
## <a name="remarks"></a>Notas  
 El `Backup` comando realiza una copia del [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de datos especificada en el [objeto](../xml-elements-properties/object-element-xmla.md) elemento a un archivo de copia de seguridad y, opcionalmente, realiza copias de seguridad de las particiones remotas a los archivos de copia de seguridad remotos. Si el elemento `Object` hace referencia a un objeto distinto de una base de datos de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], se produce un error.  
  
 La información que el `Backup` realiza copias de seguridad depende del modo de almacenamiento utilizado por los objetos en la base de datos en el comando. La tabla siguiente identifica la información de la que se hace copia de seguridad en función del modo de almacenamiento utilizado.  
  
|Modo de almacenamiento|Información de la que se hace copia de seguridad|  
|------------------|-----------------------------------|  
|OLAP multidimensional (MOLAP)|Datos de origen, agregaciones y metadatos|  
|OLAP híbrido (HOLAP)|Agregaciones y metadatos|  
|OLAP relacional (ROLAP)|Metadatos|  
  
 Durante una `Backup` comando, se coloca un bloqueo compartido en el [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de datos especificada en el `Object` elemento. Libera el bloqueo compartido después de la `Backup` comando ha finalizado.  
  
 Varios `Backup` comandos se pueden ejecutar en paralelo, si los comandos están incluidos en el [paralelo](../xml-elements-properties/parallel-element-xmla.md) colección de un [Batch](batch-element-xmla.md) comando. La colección `Parallel` permite hacer copia de seguridad de una base de datos al mismo tiempo en varios archivos de copia de seguridad.  
  
 Para obtener más información acerca de la copia de seguridad y restaurar bases de datos, vea [realizar copias de seguridad, restaurar y sincronizar bases de datos &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
> [!IMPORTANT]  
>  Para cada archivo de copia de seguridad, el usuario que ejecuta el comando de copia de seguridad debe tener permiso para escribir en la ubicación de copia de seguridad especificada. Además, el usuario debe tener uno de los roles siguientes: miembro de un rol de servidor para la instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] o miembro de un rol de base de datos con permisos de Control total (Administrador) en la base de datos de la que se va a hacer una copia de seguridad.  
  
## <a name="see-also"></a>Vea también  
 [Elemento restore &#40;XMLA&#41;](restore-element-xmla.md)   
 [Elemento Synchronize &#40;XMLA&#41;](synchronize-element-xmla.md)   
 [Comandos &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
