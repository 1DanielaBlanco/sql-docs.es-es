---
title: Configurar repositorios para SQL Server en Linux | Documentos de Microsoft
description: "Comprobar y configurar repositorios de origen para SQL Server 2017 en Linux. El repositorio de origen afecta a la versión de SQL Server que se aplica durante la instalación y actualización."
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/07/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.workload: Active
ms.openlocfilehash: 82a1f6d840897311dbb52ffbbf2620c8ec3994ec
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="configure-repositories-for-installing-and-upgrading-sql-server-on-linux"></a>Configurar repositorios de instalación y actualización de SQL Server en Linux

En este artículo se describe cómo configurar el repositorio correcta para SQL Server 2017 instalaciones y actualizaciones en Linux.

> [!IMPORTANT]
> Si instaló anteriormente un CTP o versión RC de 2017 de SQL Server, debe utilizar los pasos de este artículo para registrar un repositorio de disponibilidad General (GA) y actualizar o volver a instalar. Las versiones preliminares de SQL Server 2017 no se admiten y expirarán.

## <a id="repositories"></a>Repositorios

Cuando instala SQL Server en Linux, debe configurar un repositorio de Microsoft. Este repositorio se usa para adquirir el paquete del motor de base de datos, **mssql server**y relacionados con paquetes de SQL Server. Actualmente hay tres repositorios principales:

| Repositorio | Nombre | Description |
|---|---|---|
| **Vista previa** | **mssql-server** | Repositorio de vista previa de las versiones CTP y RC de SQL Server. Este repositorio no se admite para SQL Server 2017. |
| **CU** | **mssql-server-2017** | Repositorio de SQL Server de 2017 acumulativa actualización (CU). |
| **GDR** | **mssql-server-2017-gdr** | Repositorio de SQL Server de 2017 GDR sólo las actualizaciones críticas. |

## <a id="cuversusgdr"></a>Actualización acumulativa frente a GDR

Es importante tener en cuenta que hay dos tipos principales de repositorios para cada distribución:

- **Las actualizaciones acumulativas (CU)**: repositorio de actualización acumulativa The (CU) contiene los paquetes para la versión de SQL Server base y cualquier correcciones o mejoras desde esa versión. Las actualizaciones acumulativas son específicas de una versión de lanzamiento, por ejemplo, SQL Server 2017. Se publican a un ritmo regular.

- **GDR**: repositorio el GDR contiene paquetes para la versión de SQL Server base y solo correcciones críticas y actualizaciones de seguridad desde esa versión. Estas actualizaciones también se agregan a la próxima versión CU.

Cada versión CU y GDR contiene el paquete completo de SQL Server y todas las actualizaciones anteriores para ese repositorio. Se admite la actualización desde una versión GDR a una versión CU cambiando su repositorio configurado para SQL Server. También puede [degradar](sql-server-linux-setup.md#rollback) a cualquier versión dentro de la versión principal (por ejemplo: 2017).

> [!NOTE]
> Puede actualizar desde una versión GDR a CU cambiando los repositorios de la versión en cualquier momento. Actualizar desde una CU no se admite la versión a una versión GDR. 

## <a id="configure"></a>Configurar un repositorio

Las secciones siguientes describen cómo comprobar y configurar un repositorio para las plataformas compatibles siguientes:

- [Red Hat Enterprise Server](#rhel)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#sles)

## <a id="rhel"></a>Configurar repositorios RHEL
Use los pasos siguientes para configurar repositorios en Red Hat Enterprise Server (RHEL).

### <a name="check-for-previously-configured-repositories-rhel"></a>Busque repositorios configurados previamente (RHEL)
En primer lugar, compruebe si ya se ha registrado un repositorio de SQL Server.

1. Ver los archivos en el **/etc/yum.repos.d** directorio con el siguiente comando:

   ```bash
   sudo ls /etc/yum.repos.d
   ```

2. Busque un archivo que configura el directorio de SQL Server, como **server.repo mssql**.

3. Imprimir el contenido del archivo.

   ```bash
   sudo cat /etc/yum.repos.d/mssql-server.repo
   ```

4. El **nombre** propiedad es el repositorio configurado. Puede identificar con la tabla en la [repositorios](#repositories) sección de este artículo.

### <a name="remove-old-repository-rhel"></a>Quitar el antiguo repositorio (RHEL)
Si es necesario, quite el antiguo repositorio con el siguiente comando.

```bash
sudo rm -rf /etc/yum.repos.d/mssql-server.repo
```

Este comando asume que el archivo identificado en la sección anterior se denominaba **server.repo mssql**.

### <a name="configure-new-repository-rhel"></a>Configurar nuevo repositorio (RHEL)
Configure el nuevo repositorio que se utilizará para las actualizaciones y las instalaciones de SQL Server. Utilice uno de los siguientes comandos para configurar el repositorio de su elección.

| Repositorio | Command |
|---|---|
| **CU** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
| **GDR** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |

## <a id="sles"></a>Configurar repositorios SLES
Use los pasos siguientes para configurar repositorios en SLES.

### <a name="check-for-previously-configured-repositories-sles"></a>Busque repositorios configurados previamente (SLES)
En primer lugar, compruebe si ya se ha registrado un repositorio de SQL Server.

1. Use **zypper información** para obtener información acerca de cualquier repositorio configurado previamente.

   ```bash
   sudo zypper info mssql-server
   ```

2. El **repositorio** propiedad es el repositorio configurado. Puede identificar con la tabla en la [repositorios](#repositories) sección de este artículo.

### <a name="remove-old-repository-sles"></a>Quitar el antiguo repositorio (SLES)
Si es necesario, quite el antiguo repositorio. Utilice uno de los siguientes comandos según el tipo de repositorio configurado previamente.

| Repositorio | Comando para quitar |
|---|---|
| **Vista previa** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
| **CU** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017'` |
| **GDR** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017-gdr'`|

### <a name="configure-new-repository-sles"></a>Configurar nuevo repositorio (SLES)
Configure el nuevo repositorio que se utilizará para las actualizaciones y las instalaciones de SQL Server. Utilice uno de los siguientes comandos para configurar el repositorio de su elección.

| Repositorio | Command |
|---|---|
| **CU** | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
| **GDR** | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |

## <a id="ubuntu"></a>Configurar repositorios de Ubuntu
Use los pasos siguientes para configurar repositorios en Ubuntu.

### <a name="check-for-previously-configured-repositories-ubuntu"></a>Busque repositorios configurados previamente (Ubuntu)
En primer lugar, compruebe si ya se ha registrado un repositorio de SQL Server.

1. Ver el contenido de la **/etc/apt/sources.list** archivo.

   ```bash
   sudo cat /etc/apt/sources.list
   ```

2. Examine la dirección URL del paquete para servidor mssql. Puede identificar con la tabla en la [repositorios](#repositories) sección de este artículo.

### <a name="remove-old-repository-ubuntu"></a>Quitar el antiguo repositorio (Ubuntu)
Si es necesario, quite el antiguo repositorio. Utilice uno de los siguientes comandos según el tipo de repositorio configurado previamente.

| Repositorio | Comando para quitar |
|---|---|
| **Vista previa** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` 
| **CU** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017 xenial main'` | 
| **GDR** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr xenial main'` |

### <a name="configure-new-repository-ubuntu"></a>Configurar nuevo repositorio (Ubuntu)
Configure el nuevo repositorio que se utilizará para las actualizaciones y las instalaciones de SQL Server.

1. Importar las claves GPG repositorio público.

   ```bash
   sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Utilice uno de los siguientes comandos para configurar el repositorio de su elección.

   | Repositorio | Command |
   |---|---|
   | **CU** | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"` |
   | **GDR** | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)"` |

3. Ejecutar **apt Obtenga actualización**.

   ```bash
   sudo apt-get update
   ```

## <a name="next-steps"></a>Pasos siguientes

Después de haber configurado el repositorio correcto, puede continuar con [instalar](sql-server-linux-setup.md#platforms) o [actualizar](sql-server-linux-setup.md#upgrade) SQL Server y los relacionados con los paquetes desde el repositorio de nuevo.

> [!IMPORTANT]
> En este punto, si opta por utilizar uno de los artículos de la instalación, como el [tutoriales](sql-server-linux-setup.md#platforms), recuerde que ya ha configurado el repositorio de destino. No repita este paso en los tutoriales. Esto es especialmente cierto si configura el repositorio GDR, ya que los tutoriales usan el repositorio de CU.

> [!IMPORTANT]
> Cualquier versión de SQL Server 2017 anteriores a la versión de CTP 2.1 debe actualizarse al menos 2.1 antes de actualizar a la versión de GA. Otra opción consiste en las bases de datos de copia de seguridad, desinstale la versión anterior y, a continuación, realizar una instalación nueva de una versión de GA.

Para obtener más información sobre cómo instalar SQL Server 2017 en Linux, consulte [Guía de instalación para SQL Server en Linux](sql-server-linux-setup.md).
