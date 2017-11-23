---
title: "Entradas del registro para los orígenes de datos | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- subkeys [ODBC]
- data sources [ODBC], registry entries
- registry entries for data sources [ODBC], about registry entries
- data sources [ODBC], configuring
- registry entries for data sources [ODBC]
ms.assetid: 78aaa3d3-d081-4550-80e3-720c910d5996
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 96e3a3e03e0a3b8f995323c81f6052bf41d16dbd
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2017
---
# <a name="registry-entries-for-data-sources"></a>Entradas del registro para los orígenes de datos
> [!NOTE]  
>  A partir de Windows XP y Windows Server 2003, ODBC se incluye en el sistema operativo de Windows. Solo explícitamente debe instalar ODBC en versiones anteriores de Windows.  
  
 El instalador DLL mantiene información en el registro de cada origen de datos. En Microsoft Windows NT o Windows 2000 y Microsoft Windows 95 o Windows 98, esta información se almacena en las subclaves bajo una de las dos claves del registro siguientes:  
  
 HKEY_LOCAL_MACHINE  
  
 SOFTWARE  
  
 ODBC  
  
 ODBC.ini  
  
 HKEY_CURRENT_USER  
  
 SOFTWARE  
  
 ODBC  
  
 ODBC.ini  
  
 Clave que se usa depende de si el origen de datos es un *origen de datos del sistema,* que está disponible para todos los usuarios, o un *origen de datos de usuario,* que solo está disponible para el usuario actual. Orígenes de datos del sistema se almacenan en el árbol HKEY_LOCAL_MACHINE y orígenes de datos de usuario se almacenan en el árbol HKEY_CURRENT_USER. En todos los demás aspectos, los orígenes de datos del sistema y los orígenes de datos de usuario son idénticos.  
  
 Esta sección contiene los temas siguientes.  
  
-   [Subclave de orígenes de datos de ODBC](../../../odbc/reference/install/odbc-data-sources-subkey.md)  
  
-   [Subclaves de la especificación del origen de datos](../../../odbc/reference/install/data-source-specification-subkeys.md)  
  
-   [Subclave predeterminada](../../../odbc/reference/install/default-subkey.md)  
  
-   [Subclave ODBC](../../../odbc/reference/install/odbc-subkey.md)
