---
title: Administrar modelos (datos de SQL Server a los complementos de minería de datos) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mining models, importing
- mining models, deleting
- mining models, managing
- mining models, training
- mining models, processing
- mining models, exporting
ms.assetid: c11380f0-7c24-4668-9cdf-9c53e4aff665
caps.latest.revision: 18
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f5b0ebb3690bd74e0e058a1ede2497c0b404d143
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161456"
---
# <a name="manage-models-sql-server-data-mining-add-ins"></a>Administrar modelos (Complementos de minería de datos de SQL Server)
  ![Botón de administrar modelos, cinta de opciones minería de datos](media/dmc-manage.gif "botón Administrar modelos, cinta de opciones minería de datos")  
  
 El **administrar modelos** cuadro de diálogo le permite interactuar con modelos de minería de datos existentes y las estructuras de minería de datos que se almacenan en el [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] servidor al que está conectado actualmente. También puede ver y administrar estructuras y modelos temporales que se han creado durante la sesión actual. Si ha usado tanto modelos de sesión como modelos almacenados en un servidor, todos ellos estarán visibles en el cuadro de diálogo.  
  
## <a name="using-the-manage-models-wizard"></a>Usar el Asistente para administrar modelos  
 Al hacer clic en **administrar modelos**, **administrar estructuras de minería de datos y modelos** abre el cuadro de diálogo, que proporciona acceso a la siguiente funcionalidad para administrar estructuras y modelos de minería de datos existentes:  
  
-   Cambiar el nombre de un modelo o una estructura de minería de datos  
  
-   Eliminar un modelo o una estructura de minería de datos  
  
-   Borrar un modelo o una estructura de minería de datos  
  
-   Procesar una estructura de minería de datos con datos nuevos o existentes  
  
-   Exportar o importar un modelo o una estructura de minería de datos  
  
> [!NOTE]  
>  En este cuadro de diálogo no se pueden crear consultas o modelos. Para crear una nueva estructura de minería de datos, use uno de los asistentes incluidos en el cliente de minería de datos para Excel, o utilice el **Editor de consultas avanzadas de minería de datos**.  
  
### <a name="requirements"></a>Requisitos  
 Para administrar modelos de minería de datos, primero debe crear una conexión a una instancia de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. La conexión es necesaria incluso aunque se trabaje con modelos de sesión almacenados en un archivo temporal. Para obtener más información acerca de cómo crear o cambiar una conexión, consulte [conectarse a los datos de origen &#40;cliente de minería de datos para Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
 Si la instancia de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] a la que se conecta no contiene estructuras ni modelos de minería de datos, puede crearlos usando los asistentes y demás herramientas que le proporciona este complemento. También puede crear nuevos modelos mediante el **Editor de la avanzada de modelo de minería de datos**.  
  
## <a name="see-also"></a>Vea también  
 [Documentar modelos de minería de datos &#40;datos complementos de minería de datos para Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md)   
 [Implementar y ampliar modelos de minería de datos &#40;datos complementos de minería de datos para Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)   

  
