---
title: "Información general de SQL Server en Linux | Documentos de Microsoft"
description: "Este artículo describe cómo SQL Server se ejecuta en Linux y proporciona información sobre cómo obtener más información."
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/21/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 9dcc6a90-0add-42c2-815b-862e4e2a21ac
ms.workload: Active
ms.openlocfilehash: d0047c61b5b02ad392da9e4b88deedc2033d070a
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2018
---
# <a name="sql-server-on-linux"></a>SQL Server en Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

2017 de SQL Server se ejecuta ahora en Linux. Es el mismo motor de base de datos de SQL Server, con muchas características y servicios, independientemente de su sistema operativo similar.

## <a name="install"></a>Install

Para comenzar, instale a SQL Server en Linux con uno de los siguientes tutoriales:

- [Instalar en Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Instalar en SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Instalar en Ubuntu](quickstart-install-connect-ubuntu.md)
- [Ejecutar en Docker](quickstart-install-connect-docker.md)
- [Aprovisionar una máquina virtual de SQL en Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

> [!NOTE]
> Docker sí se ejecuta en varias plataformas, lo que significa que puede ejecutar la imagen de Docker en Linux, Mac y Windows.

## <a name="connect"></a>Conectar

Después de la instalación, conéctese a la instancia de SQL Server en su equipo Linux. Puede conectarse localmente o y de forma remota con una variedad de herramientas y los controladores. Los tutoriales muestran cómo usar el [sqlcmd](sql-server-linux-setup-tools.md) herramienta de línea de comandos. Otras herramientas incluyen lo siguiente:

| Herramienta | Tutorial |
|-----|-----|
| Código de Visual Studio (frente a código) | [Usar código de VS con SQL Server en Linux](sql-server-linux-develop-use-vscode.md) |
| SQL Server Management Studio (SSMS) | [Usar SSMS en Windows para conectarse a SQL Server en Linux](sql-server-linux-develop-use-ssms.md) |
| SQL Server Data Tools (SSDT) | [Usar SSDT con SQL Server en Linux](sql-server-linux-develop-use-ssdt.md) |

## <a name="explore"></a>Explorar

SQL Server 2017 tiene el mismo motor de base de datos subyacente en todas las plataformas admitidas, incluidos Linux. Por lo que muchas características y capacidades existentes funcionan de la misma forma en Linux. Esta área de la documentación expone algunas de estas características desde la perspectiva de Linux. También resalta las áreas que tienen requisitos únicos en Linux.

Si ya está familiarizado con SQL Server, revise la [notas de la versión](sql-server-linux-release-notes.md) de directrices generales y problemas conocidos de esta versión. A continuación, examine [what's new for SQL Server en Linux](sql-server-linux-whats-new.md) como [Novedades de SQL Server 2017 general](../sql-server/what-s-new-in-sql-server-2017.md). Para obtener respuestas a las preguntas más frecuentes, consulte el [SQL Server en Linux preguntas más frecuentes sobre](sql-server-linux-faq.md).

##  <a name="infotipmediageneralinfotippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](./media/general/info_tip.png) Comunicación con el equipo de ingeniería de SQL Server

- [Cambio de la pila de DBA](https://dba.stackexchange.com/questions/tagged/sql-server): formular preguntas de administración de base de datos
- [Desbordamiento de pila](http://stackoverflow.com/questions/tagged/sql-server): formular preguntas de desarrollo
- [Foros de MSDN](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver): hacer preguntas técnicas
- [Enviar comentarios](https://feedback.azure.com/forums/908035-sql-server): informe de errores y la característica de solicitud
- [Reddit](https://www.reddit.com/r/SQLServer/): analizar SQL Server
