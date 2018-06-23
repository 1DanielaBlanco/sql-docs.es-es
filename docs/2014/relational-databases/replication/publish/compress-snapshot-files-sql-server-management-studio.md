---
title: Comprimir archivos de instantáneas (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snapshots [SQL Server replication], compressed
- snapshot replication [SQL Server], compressed snapshots
ms.assetid: 174ade3e-74a1-4e67-a6da-b874be3ff50f
caps.latest.revision: 34
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 70b8ec331bcc1d14174a4efb9d9808820ad62c04
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36203609"
---
# <a name="compress-snapshot-files-sql-server-management-studio"></a>Comprimir archivos de instantáneas (SQL Server Management Studio)
  Especifique que se deben comprimir los archivos en la página **Instantánea** del cuadro de diálogo **Propiedades de la publicación: \<publicación>**. Para obtener más información sobre el acceso a este cuadro de diálogo, vea [View and Modify Publication Properties](view-and-modify-publication-properties.md).  
  
### <a name="to-compress-snapshot-files"></a>Para comprimir archivos de instantáneas  
  
1.  En la página **Instantánea** del cuadro de diálogo **Propiedades de la publicación: \<Publicación>**:  
  
    1.  Seleccione **Poner los archivos en la siguiente carpeta**y haga clic en **Examinar** para navegar al directorio, o bien escriba la ruta de acceso al directorio en el que deben almacenarse los archivos de instantáneas.  
  
        > [!NOTE]  
        >  El Agente de instantáneas debe tener permisos de escritura para el directorio especificado y el Agente de distribución o de mezcla debe tener permisos de lectura. Si utiliza suscripciones de extracción, debe especificar un directorio compartido como ruta de acceso, según la convención de nomenclatura universal (UNC), por ejemplo \\\nombreDeEquipo\instantánea. Para más información, vea [Proteger la carpeta de instantáneas](../security/secure-the-snapshot-folder.md).  
  
    2.  Desactive la casilla **Poner los archivos en la carpeta predeterminada** , a menos que necesite copiar los archivos de instantáneas en ambas ubicaciones.  
  
        > [!NOTE]  
        >  Si esta casilla está activada, los archivos almacenados en la carpeta predeterminada no se comprimen. Los archivos comprimidos solo se pueden almacenar en la ubicación alternativa especificada en el paso anterior.  
  
2.  Active **Comprimir archivos de instantánea en esta carpeta**.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Configurar propiedades de instantáneas &#40;programación de la replicación con Transact-SQL&#41;](configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Cambiar las propiedades de la publicación y de los artículos](change-publication-and-article-properties.md)   
 [Instantáneas comprimidas](../compressed-snapshots.md)   
 [Inicializar una suscripción con una instantánea](../initialize-a-subscription-with-a-snapshot.md)  
  
  