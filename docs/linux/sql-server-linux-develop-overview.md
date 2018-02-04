---
title: Desarrollar aplicaciones para SQL Server en Linux | Documentos de Microsoft
description: 
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.technology: database-engine
ms.assetid: 758cb738-b018-465b-9ab0-59a24b892e66
ms.workload: On Demand
ms.openlocfilehash: 9bfd1b4f30593fa6ae4d17ec92bfa0047ea751bc
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-get-started-developing-applications-for-sql-server-on-linux"></a>Cómo empezar a desarrollar aplicaciones para SQL Server en Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Puede crear aplicaciones que se conectan a y usar SQL Server 2017 en Linux desde una variedad de lenguajes de programación, como C#, Java, Node.js, PHP, Python, Ruby y C++. También puede utilizar marcos web populares y marcos de trabajo de asignación relacional de objetos (ORM).

> [!VIDEO https://channel9.msdn.com/events/Connect/2017/T153/player]

> [!TIP]
> Estas mismas opciones de desarrollo también permiten dirigidas a SQL Server en otras plataformas. Las aplicaciones pueden tener como destino SQL Server que se ejecutan de forma local o en la nube, en Docker, Windows o Linux en macOS. O bien, puede tener como destino base de datos de SQL Azure y almacenamiento de datos de SQL Azure.

## <a name="try-the-tutorials"></a>Utilice los tutoriales

La mejor manera de empezar a trabajar y crear aplicaciones con SQL Server es Pruébelo usted mismo.

- Vaya a [tutoriales de introducción](http://aka.ms/sqldev).
- Seleccionar la plataforma de desarrollo y de idioma.
- Pruebe los ejemplos de código.

> [!TIP]
> Si desea desarrollar para SQL Server 2017 en Docker, eche un vistazo a la **macOS** tutoriales.

## <a name="create-new-applications"></a>Crear nuevas aplicaciones

Si va a crear una nueva aplicación, eche un vistazo a una lista de los [bibliotecas de conectividad](sql-server-linux-develop-connectivity-libraries.md) para obtener un resumen de los conectores y entornos populares disponibles para varios lenguajes de programación.

## <a name="use-existing-applications"></a>Utilizar las aplicaciones existentes

Si tiene una aplicación de base de datos existente, simplemente puede cambiar la cadena de conexión al destino 2017 de SQL Server en Linux. Asegúrese de que conozca el [problemas conocidos](sql-server-linux-release-notes.md) en SQL Server 2017 en Linux.

## <a name="use-existing-sql-tools-on-windows-with-sql-server-on-linux"></a>Use las herramientas SQL existentes en Windows con SQL Server en Linux

Herramientas que se ejecutan actualmente en Windows como SSMS, SSDT y PowerShell, también funcionan con SQL Server 2017 en Linux. Aunque no ejecuten de forma nativa en Linux, igualmente podrá administrar las instancias remotas de SQL Server en Linux. 

Vea los temas siguientes para obtener más información:

- [SQL Server Management Studio (SSMS)](sql-server-linux-develop-use-ssms.md)
- [SQL Server Data Tools (SSDT)](sql-server-linux-develop-use-ssdt.md)
- [PowerShell SQL](sql-server-linux-manage-powershell.md)

> [!Note] 
> Asegúrese de que está usando las versiones más recientes de estas herramientas para una mejor experiencia.

## <a name="use-new-sql-tools-for-linux"></a>Usar nuevas herramientas SQL para Linux

Puede usar la nueva [mssql extensión](https://aka.ms/mssql-marketplace) para [código de Visual Studio](https://code.visualstudio.com) en Linux, Mac OS y Windows. Para ver un tutorial paso a paso, vea el tutorial siguiente:

- [Usar Visual Studio Code](sql-server-linux-develop-use-vscode.md)

También puede usar nuevas herramientas de línea de comandos que son nativos de Linux. Estas herramientas incluyen lo siguiente:

- [sqlcmd](../tools/sqlcmd-utility.md)
- [bcp](sql-server-linux-migrate-bcp.md)
- [mssql-conf](sql-server-linux-configure-mssql-conf.md)

## <a name="next-steps"></a>Pasos siguientes

Para comenzar, instale a SQL Server en Linux con uno de los siguientes tutoriales:

- [Instalar en Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Instalar en SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Instalar en Ubuntu](quickstart-install-connect-ubuntu.md)
- [Ejecutar en Docker](quickstart-install-connect-ubuntu.md)
