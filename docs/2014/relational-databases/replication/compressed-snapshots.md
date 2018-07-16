---
title: Instantáneas comprimidas | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], compressed
- snapshot replication [SQL Server], compressed snapshots
- compressed snapshots [SQL Server replication]
ms.assetid: 979ffa7c-3a88-4e70-8cf2-b8d452fd7a7f
caps.latest.revision: 33
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 34a397f4c6597751d50aa676f07d42cc694e9c39
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37303695"
---
# <a name="compressed-snapshots"></a>Instantáneas comprimidas
  La compresión de los archivos de instantáneas es apropiada para transferir instantáneas a través de una red lenta o para guardarlas en un soporte extraíble, cuando la instantánea sin comprimir es demasiado grande. La compresión de los archivos de instantáneas resulta útil en estos casos, pero aumenta el tiempo necesario para generar y aplicar la instantánea.  
  
 Los archivos de instantáneas comprimidos se escriben en formato de archivo CAB de [!INCLUDE[msCoName](../../includes/msconame-md.md)] , que permite comprimir archivos de hasta 2 GB (si el archivo de instantánea tiene más de 2 GB, no se puede comprimir). Para comprimir archivos, es necesario copiarlos a otra carpeta de instantáneas (los archivos de la carpeta de instantáneas predeterminada no se pueden comprimir). Para más información sobre las ubicaciones alternativas para las carpetas de instantáneas, vea [Ubicaciones alternativas para las carpetas de instantáneas](alternate-snapshot-folder-locations.md).  
  
 Los archivos se descomprimen en la ubicación en la que se ejecuta el Agente de distribución o de mezcla; por lo general, se usan suscripciones de extracción con las instantáneas comprimidas para descomprimir los archivos en el suscriptor. Cuando el suscriptor recibe un archivo comprimido, lo copia inicialmente a una ubicación temporal. Una vez copiado el archivo comprimido en el suscriptor, la utilidad CAB descomprime los archivos de instantáneas de uno en uno, en orden. El espacio necesario en el suscriptor es el tamaño del archivo comprimido más el del archivo más grande sin comprimir.  
  
> [!NOTE]  
>  En algunos casos, las instantáneas comprimidas pueden mejorar el rendimiento de la transferencia de archivos de instantáneas en la red. No obstante, la compresión de instantáneas requiere que el Agente de instantáneas realice un procesamiento adicional al generar los archivos de instantáneas, y otro procesamiento adicional por parte del Agente de distribución o del Agente de mezcla al aplicar los archivos de instantáneas. Esto puede ralentizar, en algunos casos, la generación de instantáneas y aumentar el tiempo de aplicación de una instantánea. Además, las instantáneas comprimidas no se pueden reanudar si se produce un error de red; por tanto, no son adecuadas para redes no confiables. Cuando utilice instantáneas comprimidas en una red, tenga en cuenta estos inconvenientes.  
  
 **Para comprimir y entregar archivos de instantáneas**  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Comprimir archivos de instantáneas &#40;SQL Server Management Studio&#41;](publish/compress-snapshot-files-sql-server-management-studio.md)  
  
-   Programación de la replicación con [!INCLUDE[tsql](../../includes/tsql-md.md)]: [Configurar propiedades de instantáneas &#40;programación de la replicación con Transact-SQL&#41;](publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
## <a name="see-also"></a>Vea también  
 [Inicializar una suscripción con una instantánea](initialize-a-subscription-with-a-snapshot.md)   
 [Opciones de instantánea](snapshot-options.md)  
  
  
