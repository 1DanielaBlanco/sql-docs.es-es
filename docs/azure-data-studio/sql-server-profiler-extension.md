---
title: Extensión de Azure Data Studio SQL Server Profiler | Microsoft Docs
description: Extensión de SQL Server Profiler (versión preliminar) para Azure Data Studio
ms.custom: tools|sos
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.prod_service: sql-tools
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: f92391c3d18648555a0c65d55915bf6752c195b8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "48039003"
---
# <a name="sql-server-profiler-extension-preview"></a>Extensión de SQL Server Profiler (versión preliminar)

La extensión de SQL Server Profiler (versión preliminar) proporciona una solución de seguimiento de SQL Server sencilla similar a SQL Server Management Studio (SSMS) Profiler excepto compiladas con XEvents. SQL Server Profiler es muy fácil de usar y tiene valores por defecto buenos para las configuraciones más comunes de seguimiento. La experiencia de usuario está optimizado para examinar a través de eventos y ver el texto de Transact-SQL (T-SQL) asociado. El Profiler de SQL Server para Azure Data Studio también se da por supuesto valores por defecto buenos para la recopilación de actividades de ejecución de Transact-SQL con una experiencia de usuario fácil de usar. Esta extensión está actualmente en versión preliminar.

**SQL Profiler-casos de uso comunes:**

- Seguir los pasos de consultas con problemas para buscar la causa de los mismos.
- Buscar y diagnosticar consultas de ejecución lenta.
- Captura de la serie de instrucciones de Transact-SQL que conducen a un problema.
- Supervisión del rendimiento de SQL Server para optimizar las cargas de trabajo.
- Establecer correlaciones entre contadores de rendimiento para diagnosticar problemas.


## <a name="install-the-sql-server-profiler-extension"></a>Instalar la extensión de SQL Server Profiler

1. Para abrir el Administrador de extensiones y tener acceso a las extensiones disponibles, seleccione el icono de extensiones o **extensiones** en el **vista** menú.
2. Seleccione una extensión disponible para ver sus detalles.

   ![Administrador de extensiones del generador de perfiles](media/extensions/sql-server-profiler-extension/profiler-extension.png)

1. Seleccione la extensión que desee y **instalar** lo.
2. Seleccione **recarga** para habilitar la extensión (solo es necesario instalar una extensión por primera vez).

## <a name="start-profiler"></a>Iniciar Profiler

1. Para iniciar a Profiler, asegúrese en primer lugar una conexión a un servidor en la pestaña servidores.
2. Después de realizar una conexión, escriba **Alt + P** iniciar Profiler.
3. Para iniciar Profiler, escriba **Alt + S.** Ahora puede comenzar a observar los eventos extendidos.
    ![Administrador de extensiones del generador de perfiles](media/extensions/sql-server-profiler-extension/view-profiler.png)    
1. Para detener Profiler, escriba **Alt + S.** Esta tecla de acceso rápido es un botón de alternancia.

## <a name="next-steps"></a>Pasos siguientes

Para aprender más sobre Profiler y eventos extendidos, vea [eventos extendidos](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events).





