---
title: Componentes de configuración | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], configuring
ms.assetid: 0b68ff48-12e4-41aa-b9e2-b39ed5023ea7
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9c15accf395a33a1af42fe65a3c15612402e381d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="configuration-components"></a>Componentes de configuración
> [!NOTE]  
>  A partir de Windows XP y Windows Server 2003, ODBC se incluye en el sistema operativo de Windows. Solo explícitamente debe instalar ODBC en versiones anteriores de Windows.  
  
 Orígenes de datos se configuran mediante el instalador de DLL, que en el controlador llama a su vez el programa de instalación archivos DLL y el programa de instalación de traductor DLL según sean necesarios. El instalador DLL se bien invocar directamente desde el Panel de Control o carga y se llama a otro programa, conocido como el *programa administración*. En la siguiente ilustración muestra la relación entre los componentes de configuración.  
  
 ![Relación entre componentes de configuración](../../../odbc/reference/install/media/pr30.gif "pr30")  
  
 Para obtener más información acerca de estos componentes, vea los temas siguientes al final de esta sección.  
  
-   [Programa de instalación](../../../odbc/reference/install/setup-program.md)  
  
-   [DLL instalador](../../../odbc/reference/install/installer-dll.md)  
  
-   [DLL de instalación del controlador](../../../odbc/reference/install/driver-setup-dll.md)  
  
## <a name="see-also"></a>Vea también  
 [Componentes de instalación](../../../odbc/reference/install/installation-components.md)
