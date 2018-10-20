---
title: Configuración de Firewall para SQL Server Machine Learning Services | Microsoft Docs
description: Cómo configurar el firewall para SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: d2bf36ea9a7c7a0b193dc4613f6a36f58e66014a
ms.sourcegitcommit: 13d98701ecd681f0bce9ca5c6456e593dfd1c471
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2018
ms.locfileid: "49419060"
---
# <a name="firewall-configuration-for-sql-server-machine-learning-services"></a>Configuración de Firewall para SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

En este artículo se enumera las consideraciones de configuración de firewall que el administrador o el arquitecto debe tener en cuenta al usar servicios de machine learning.

## <a name="default-firewall-rules"></a>Reglas de firewall predeterminada

De forma predeterminada, el programa de instalación de SQL Server deshabilita las conexiones salientes mediante la creación de reglas de firewall.

En SQL Server 2016 y 2017, estas reglas se basan en cuentas de usuario local, donde el programa de instalación crea una regla de salida para **SQLRUserGroup** que deniega el acceso de red a sus miembros (cada cuenta de trabajo se muestra como una entidad de seguridad local, sujeto a la regla. Para obtener más información sobre SQLRUserGroup, consulte [información general de seguridad para el marco de extensibilidad en SQL Server Machine Learning Services](../../advanced-analytics/concepts/security.md#sqlrusergroup).

En SQL Server 2019, como parte de la migración a AppContainers, hay nuevas reglas de firewall basadas en AppContainer SIDs: uno para cada uno de los 20 AppContainers creado por el programa de instalación de SQL Server. Convenciones de nomenclatura para el nombre de regla de firewall son **bloquear el acceso de red para AppContainer 00 en la instancia de SQL Server MSSQLSERVER**, donde 00 es el número de AppContainer (00-20 de forma predeterminada) y MSSQLSERVER es el nombre de la consulta SQL Instancia del servidor.

> [!Note]
> Si se requieren las llamadas de red, puede deshabilitar las reglas de salida en el Firewall de Windows.

## <a name="restrict-network-access"></a>Restringir el acceso de red

En una instalación predeterminada, se utiliza una regla de firewall de Windows para bloquear todo el acceso de red saliente desde procesos externos en tiempo de ejecución. Deben crearse reglas de Firewall para impedir que los procesos externos en tiempo de ejecución descarga de paquetes o realicen otras llamadas de red que podrían ser malintencionadas.

Si usa otro programa de firewall, también puede crear reglas para bloquear la conexión de red saliente para tiempos de ejecución externos, estableciendo reglas para las cuentas de usuario local o para el grupo representado por el grupo de cuentas de usuario.

Se recomienda encarecidamente que active Firewall de Windows (u otro firewall de su elección) para impedir el acceso a la red sin restricciones por los tiempos de ejecución de R o Python.

## <a name="next-steps"></a>Pasos siguientes

[Configurar firewall de Windows para las conexiones entrantes](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)