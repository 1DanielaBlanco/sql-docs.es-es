---
title: Configuración de área de trabajo y usuario Studio de datos de Azure | Microsoft Docs
description: Cómo modificar la configuración de área de trabajo y usuario de Azure Data Studio.
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: e446d117bd56cb0c3607eeaf40522800d82e8a7e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "48039051"
---
# <a name="user-and-workspace-settings"></a>Usuario y la configuración de área de trabajo

Es fácil de configurar [!INCLUDE[name-sos](../includes/name-sos-short.md)] a su gusto a través de configuración. Casi todas las partes de [!INCLUDE[name-sos](../includes/name-sos-short.md)]del editor, la interfaz de usuario y comportamiento funcional tiene opciones puede modificar.

[!INCLUDE[name-sos](../includes/name-sos-short.md)] proporciona dos ámbitos diferentes para la configuración:

* **Usuario** esta configuración se aplica globalmente a cualquier instancia de [!INCLUDE[name-sos](../includes/name-sos-short.md)] abrir.
* **Área de trabajo** configuración de área de trabajo son valores específicos de una carpeta en el equipo y solo están disponibles cuando la carpeta se abre en la barra lateral de explorador. Configuración definida en este ámbito invalida el ámbito del usuario.

## <a name="creating-user-and-workspace-settings"></a>Creación de usuario y la configuración de área de trabajo

El comando de menú **archivo** > **preferencias** > **configuración** (**código**  >  **Preferencias** > **configuración** en Mac) proporciona el punto de entrada para configurar la configuración de usuario y el área de trabajo. Se proporcionan con una lista de la configuración predeterminada. Copiar cualquier configuración que desea cambiar a la correspondiente `settings.json` archivo. Las pestañas de la derecha le permite alternar rápidamente entre los archivos de configuración de usuario y el área de trabajo.

También puede abrir la configuración de usuario y del área de trabajo desde el **paleta de comandos** (**Ctrl + Mayús + P**) con **preferencias: abra Configuración de usuario** y  **Preferencias: Abrir Configuración de área de trabajo** o use el método abreviado de teclado (**Ctrl +,**).

El siguiente ejemplo deshabilita los números de línea en el editor y configura las líneas de código que se les aplica sangría automáticamente.

![Configuración de ejemplo](media/settings/sample-settings.png)

Se vuelven a cargar los cambios de configuración por [!INCLUDE[name-sos](../includes/name-sos-short.md)] después modificado `settings.json` se guarda el archivo.

>**Nota:** configuración de área de trabajo es útiles para compartir la configuración específica del proyecto a través de un equipo.

## <a name="settings-file-locations"></a>Ubicaciones de archivo de configuración

Dependiendo de la plataforma, el archivo de configuración de usuario se encuentra aquí:

* **Windows** `%APPDATA%\sqlops\User\settings.json`
* **Mac** `$HOME/Library/Application Support/sqlops/User/settings.json`
* **Linux** `$HOME/.config/sqlops/User/settings.json`

El archivo de configuración de área de trabajo se encuentra en la `.[!INCLUDE[name-sos](../includes/name-sos-short.md)]` carpeta del proyecto.

## <a name="hot-exit"></a>Salida de acceso frecuente

Azure Data Studio recuerda los cambios no guardados en archivos cuando se cierra de forma predeterminada. Esto es lo mismo que la característica hot salir en Visual Studio Code.

De forma predeterminada, la salida activo está desactivada. Habilitar salida hot editando el `files.hotExit` configuración. Para obtener más información, consulte [activo de salida (en la documentación de Visual Studio Code)](https://code.visualstudio.com/docs/editor/codebasics#_hot-exit).


## <a name="tab-color"></a>Color de etiqueta

Para simplificar la identificación de las conexiones que se trabaja con, las pestañas abiertas en el editor pueden tener sus colores establecidos para que coincida con el color del grupo de servidores al que pertenece la conexión. De forma predeterminada, los colores de pestaña están desactivados de forma predeterminada. Habilitar los colores de pestaña editando el `sql.tabColorMode` configuración.

## <a name="additional-resources"></a>Recursos adicionales

Dado que [!INCLUDE[name-sos](../includes/name-sos-short.md)] hereda su configuración de usuario y el área de trabajo en la funcionalidad de Visual Studio Code, información detallada acerca de la configuración es la [valores para Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings) artículo.
