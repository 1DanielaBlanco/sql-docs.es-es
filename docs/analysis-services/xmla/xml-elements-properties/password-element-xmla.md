---
title: Elemento Password (XMLA) | Documentos de Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 488b406a6378853ecf34fce5405669e28420bde4
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
---
# <a name="password-element-xmla"></a>Elemento Password (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Determina la contraseña que va a usar el elemento primario [copia de seguridad](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) o [restaurar](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) comando para cifrar o descifrar un archivo de copia de seguridad.  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <Password>...</Password>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Características de los elementos  
  
|Característica|Descripción|  
|--------------------|-----------------|  
|Tipo y longitud de los datos|Cadena|  
|Valor predeterminado|Ninguno|  
|Cardinalidad|0-1: Elemento opcional que puede aparecer solo una vez.|  
  
## <a name="element-relationships"></a>Relaciones del elemento  
  
|Relación|Elemento|  
|------------------|-------------|  
|Elementos primarios|[Copia de seguridad](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [restaurar](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Elementos secundarios|Ninguno|  
  
## <a name="remarks"></a>Comentarios  
 Para los comandos **Backup** , si el elemento **Password** no está incluido o contiene una cadena vacía, no se cifra el archivo de copia de seguridad.  
  
 Para los comandos **Restore** , si el elemento **Password** no está incluido o contiene una cadena vacía y se intenta restaurar un archivo de copia de seguridad cifrado, se producirá un error.  
  
 Si los elementos **Location** están incluidos en un comando **Backup** o en un comando **Restore** , el mismo elemento **Password** se utiliza tanto para los archivos de copia de seguridad como para los archivos de copia de seguridad remota. Para obtener más información acerca de los archivos de copia de seguridad remotos, consulte [realizar copias de seguridad, restaurar y sincronizar bases de datos &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Vea también  
 [Elemento location &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)   
 [Propiedades & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
