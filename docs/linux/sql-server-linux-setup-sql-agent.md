---
title: Instalación del Agente SQL Server en Linux | Microsoft Docs
description: En este artículo se describe cómo instalar al Agente SQL Server en Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 77f16adc-e6cb-4a57-82f3-7b9780369868
ms.openlocfilehash: af15f6243dc29fc3c7596a758295cc53c66a55c0
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2018
ms.locfileid: "46713567"
---
# <a name="install-sql-server-agent-on-linux"></a>Instalación del Agente SQL Server en Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

 El [del Agente SQL Server](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent) ejecuta los trabajos programados de SQL Server. A partir de SQL Server 2017 CU4, Agente SQL Server se incluye con el **mssql-server** empaquetar y está deshabilitada de forma predeterminada. Para obtener información sobre las características compatibles con esta versión del Agente SQL Server junto con información de versión, consulte el [notas de la versión](sql-server-linux-release-notes.md).

 Instalar/habilitar al Agente SQL Server:
- [Para las versiones 2017 CU4 y versiones posteriores, habilitar al Agente SQL Server](#EnableAgentAfterCU4)
- [Para las versiones 2017 CU3 y versiones anteriores, instale al Agente SQL Server](#InstallAgentBelowCU4)


## <a name="EnableAgentAfterCU4">Para las versiones 2017 CU4 y versiones posteriores, habilitar al Agente SQL Server</a>

 Para habilitar el Agente SQL Server, siga estos pasos.

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
sudo systemctl restart mssql-server
```

> [!NOTE]
> Si no va a actualizar desde 2017 CU3 o a continuación con un agente instalado, el Agente SQL Server anterior y habilitada automáticamente los paquetes de agente se desinstalará.  

## <a name="InstallAgentBelowCU4">Para las versiones 2017 CU3 y versiones anteriores, instale al Agente SQL Server</a>

> [!NOTE]
> Las instrucciones de instalación siguientes se aplican a las versiones de SQL Server 2017 CU3 y a continuación. Antes de instalar el Agente SQL Server, en primer lugar [instalar SQL Server](sql-server-linux-setup.md#platforms). Esto configura las claves y los repositorios que se usará al instalar el **mssql-server-agent** paquete.

Instale al Agente SQL Server para su plataforma:
- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)

### <a name="RHEL">Instalar en RHEL</a>

Use los pasos siguientes para instalar el **mssql-server-agent** en Red Hat Enterprise Linux. 

```bash
sudo yum install mssql-server-agent
sudo systemctl restart mssql-server
```

Si ya tiene **mssql-server-agent** instalado, puede actualizar a la versión más reciente con los siguientes comandos:

```bash
sudo yum check-update
sudo yum update mssql-server-agent
sudo systemctl restart mssql-server
```

Si necesita una instalación sin conexión, busque la descarga del paquete del Agente SQL Server en el [notas de la versión](sql-server-linux-release-notes.md). A continuación, use los mismos pasos de instalación sin conexión se describe en el artículo [instalar SQL Server](sql-server-linux-setup.md#offline).

### <a name="ubuntu">Instalar en Ubuntu</a>

Use los pasos siguientes para instalar el **mssql-server-agent** en Ubuntu. 

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

Si ya tiene **mssql-server-agent** instalado, puede actualizar a la versión más reciente con los siguientes comandos:

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

Si necesita una instalación sin conexión, busque la descarga del paquete del Agente SQL Server en el [notas de la versión](sql-server-linux-release-notes.md). A continuación, use los mismos pasos de instalación sin conexión se describe en el artículo [instalar SQL Server](sql-server-linux-setup.md#offline).

### <a name="SLES">Instalar en SLES</a>

Use los pasos siguientes para instalar el **mssql-server-agent** en SUSE Linux Enterprise Server. 

Instalar **mssql-server-agent** 

```bash
sudo zypper install mssql-server-agent
sudo systemctl restart mssql-server
```

Si ya tiene **mssql-server-agent** instalado, puede actualizar a la versión más reciente con los siguientes comandos:

```bash
sudo zypper refresh
sudo zypper update mssql-server-agent
sudo systemctl restart mssql-server
```

Si necesita una instalación sin conexión, busque la descarga del paquete del Agente SQL Server en el [notas de la versión](sql-server-linux-release-notes.md). A continuación, use los mismos pasos de instalación sin conexión se describe en el artículo [instalar SQL Server](sql-server-linux-setup.md#offline).

## <a name="next-steps"></a>Pasos siguientes
Para obtener más información sobre cómo usar el Agente SQL Server para crear, programar y ejecutar trabajos, consulte [ejecutar un trabajo de agente SQL Server en Linux](sql-server-linux-run-sql-server-agent-job.md).
