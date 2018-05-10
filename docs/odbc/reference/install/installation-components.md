---
title: Componentes de instalación | Documentos de Microsoft
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
- installing ODBC components [ODBC], setup program
- ODBC [ODBC], component installation
ms.assetid: 9de15ca0-fe6a-4634-8709-a928d3c9cc73
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c5fe2538d1567630121f05a4798583099de7200
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="installation-components"></a>Componentes de instalación
> [!NOTE]  
>  A partir de Windows XP y Windows Server 2003, ODBC se incluye en el sistema operativo de Windows. Solo explícitamente debe instalar ODBC en versiones anteriores de Windows.  
  
 El proceso de instalación se inicia cuando el usuario ejecuta el programa de instalación. El programa de instalación funciona junto con el *installer DLL* y un *DLL de instalación de controlador* para cada controlador. El programa de instalación y el archivo DLL del programa de instalación utilizan los argumentos en la **SQLInstallDriverEx** y **SQLInstallTranslatorEx** funciones para determinar qué archivos desea copiar o eliminar para cada componente. En la siguiente ilustración muestra la relación entre estos componentes de instalación.  
  
 ![Relación entre componentes de instalación](../../../odbc/reference/install/media/pr29.gif "pr29")  
  
> [!IMPORTANT]  
>  El archivo de ODBC que se utilizó en ODBC 2. *x* para describir los archivos requeridos por cada ODBC componente no se usa en ODBC 3 *.x*. Controladores que se incluyen ODBC 3 *.x* componentes no es necesario crear un archivo de ODBC. La eliminación de **SQLInstallDriver** y **SQLInstallODBC**y el desuso de **SQLInstallTranslator**, represente ODBC innecesarios. La información del controlador que solía haber en las secciones de la palabra clave Driver de ODBC ahora se proporciona en el *lpszDriver* argumento en **SQLInstallDriverEx**. La información de traductor que solía haber en el [traductor ODBC] y secciones de la especificación de traductor de ODBC ahora se proporciona en el *lpszTranslator* argumento de **SQLInstallTranslatorEx**. Estos cambios permiten que el programa de instalación de ODBC sea más portátil entre plataformas.  
  
 Para obtener más información acerca de estos componentes, vea los temas siguientes al final de esta sección.  
  
-   [Programa de instalación](../../../odbc/reference/install/setup-program.md)  
  
-   [DLL instalador](../../../odbc/reference/install/installer-dll.md)  
  
-   [DLL de instalación del controlador](../../../odbc/reference/install/driver-setup-dll.md)
