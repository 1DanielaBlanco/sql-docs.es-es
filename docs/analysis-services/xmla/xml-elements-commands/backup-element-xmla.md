---
title: Copia de seguridad de elemento (XMLA) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Backup Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Backup
- http://schemas.microsoft.com/analysisservices/2003/engine#Backup
- microsoft.xml.analysis.backup
helpviewer_keywords:
- Backup command
ms.assetid: 5bcbc14c-9db9-45b2-99de-f3a265bcb0c4
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c5617d1b0b62eabb945881041a795a1a699b4c41
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="backup-element-xmla"></a>Elemento Backup (XMLA)
  Realiza una copia de un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de datos a un archivo de copia de seguridad.  
  
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
|Elementos secundarios|[AllowOverwrite](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md), [ApplyCompression](../../../analysis-services/xmla/xml-elements-properties/applycompression-element-xmla.md), [BackupRemotePartitions](../../../analysis-services/xmla/xml-elements-properties/backupremotepartitions-element-xmla.md), [archivo](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md), [ubicaciones](../../../analysis-services/xmla/xml-elements-properties/locations-element-xmla.md), [Objeto](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md), [contraseña](../../../analysis-services/xmla/xml-elements-properties/password-element-xmla.md), [seguridad](../../../analysis-services/xmla/xml-elements-properties/security-element-xmla.md)|  
  
## <a name="remarks"></a>Comentarios  
 El **copia de seguridad** comando realiza una copia de la [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de datos especificada en el [objeto](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md) elemento a un archivo de copia de seguridad y, opcionalmente, copias de seguridad de las particiones remotas en los archivos de copia de seguridad remotos. Si el **objeto** elemento hace referencia a un objeto distinto de un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] la base de datos, se produce un error.  
  
 La información de la que hace copia de seguridad el comando **Backup** depende del modo del almacenamiento que utilicen los objetos de la base de datos. La tabla siguiente identifica la información de la que se hace copia de seguridad en función del modo de almacenamiento utilizado.  
  
|Modo de almacenamiento|Información de la que se hace copia de seguridad|  
|------------------|-----------------------------------|  
|OLAP multidimensional (MOLAP)|Datos de origen, agregaciones y metadatos|  
|OLAP híbrido (HOLAP)|Agregaciones y metadatos|  
|OLAP relacional (ROLAP)|Metadatos|  
  
 Durante una **copia de seguridad** comando, se coloca un bloqueo compartido en el [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de datos especificada en el **objeto** elemento. El bloqueo compartido se anula después de que se haya completado la ejecución del comando **Backup** .  
  
 Varios **copia de seguridad** comandos se pueden ejecutar en paralelo, si los comandos están incluidos en el [paralelo](../../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md) colección de un [lote](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) comando. La colección **Parallel** permite hacer copia de seguridad de una base de datos al mismo tiempo en varios archivos de copia de seguridad.  
  
 Para obtener más información acerca de la copia de seguridad y restaurar bases de datos, vea [realizar copias de seguridad, restauración y sincronizar bases de datos &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
> [!IMPORTANT]  
>  Para cada archivo de copia de seguridad, el usuario que ejecuta el comando de copia de seguridad debe tener permiso para escribir en la ubicación de copia de seguridad especificada. Además, el usuario debe tener uno de los roles siguientes: miembro de un rol de servidor para la instancia de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] o miembro de un rol de base de datos con permisos de Control total (Administrador) en la base de datos de la que se va a hacer una copia de seguridad.  
  
## <a name="see-also"></a>Vea también  
 [Restaurar elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Sincronizar el elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Comandos &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  

