---
title: Crear y personalizar métodos abreviados de teclado
titleSuffix: Azure Data Studio
description: Obtenga información sobre cómo crear y personalizar métodos abreviados de teclado en Azure Data Studio
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dd58bb28fe5969fcf0553576d70dd62314f5f974
ms.sourcegitcommit: 189a28785075cd7018c98e9625c69225a7ae0777
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53030259"
---
# <a name="keyboard-shortcuts-in-includename-sosincludesname-sosmd"></a>Métodos abreviados de teclado [!INCLUDE[name-sos](../includes/name-sos.md)]

En este artículo se proporciona los pasos para ver, editar y crear métodos abreviados de teclado rápidamente [!INCLUDE[name-sos](../includes/name-sos-short.md)].

Dado que [!INCLUDE[name-sos](../includes/name-sos-short.md)] hereda su funcionalidad de enlace de teclado de Visual Studio Code, información detallada acerca de las personalizaciones avanzadas, con distintas distribuciones de teclado, etc., que está en el [enlaces de teclado para Visual Studio Code](https://code.visualstudio.com/docs/getstarted/keybindings) artículo. Algunas características de enlace de teclado no estén disponibles (por ejemplo, las extensiones de mapa de teclas no se admiten en [!INCLUDE[name-sos](../includes/name-sos-short.md)]).


## <a name="open-the-keyboard-shortcuts-editor"></a>Abra el editor de métodos abreviados de teclado

Para ver todos los métodos abreviados de teclado actualmente definidas:

Abra el **métodos abreviados de teclado** editor desde la **archivo** menú: **Archivo** > **preferencias** > **métodos abreviados de teclado** (**[!INCLUDE[name-sos](../includes/name-sos-short.md)]**  >   **Preferencias** > **métodos abreviados de teclado** en Mac).

Además de mostrar los enlaces de teclado actuales, el **métodos abreviados de teclado** editor enumera los comandos disponibles que no tienen métodos abreviados de teclado definidos. El **métodos abreviados de teclado** editor le permite fácilmente cambiar, quitar, restablecer y definir nuevos enlaces de teclado.  


## <a name="edit-existing-keyboard-shortcuts"></a>Editar accesos directos de teclado existentes

Para cambiar el enlace de teclado para un método abreviado de teclado existente:

1. Busque el método abreviado de teclado que desea cambiar mediante el cuadro de búsqueda o desplazarse a través de la lista.
   > [!TIP]
   > Buscar por clave, el comando, por origen, etc. para devolver todos los métodos abreviados de teclado correspondiente.

1. Haga clic en la entrada deseada y seleccione **enlace cambiar la clave**

   ![editar el método abreviado de teclado](media/keyboard-shortcuts/change-keybinding.png)

1. Presione la combinación deseada de claves, a continuación, presione **ENTRAR** para guardarlo. 

   ![Guarde el método abreviado de teclado](media/keyboard-shortcuts/save-keybinding.png)

## <a name="create-new-keyboard-shortcuts"></a>Crear nuevos métodos abreviados de teclado

Para crear nuevos métodos abreviados de teclado:

1. Haga clic en un comando que no tiene ninguna clave de enlace y seleccione **enlace Agregar clave**.

   ![Crear método abreviado de teclado](media/keyboard-shortcuts/add-keybinding.png)

1. Presione la combinación deseada de claves, a continuación, presione **ENTRAR** para guardarlo.


