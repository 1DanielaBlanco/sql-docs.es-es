---
title: "Configuración y administración | Documentos de Microsoft"
ms.custom: 
ms.date: 05/31/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0fd4554-60c6-4181-ac4c-2e366fb434f6
caps.latest.revision: 7
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c533a35c09842221468764ef2f59e7c9cd7714d5
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="configuration-and-management"></a>Configuración y administración

Este artículo contiene vínculos a información más detallada sobre cómo configurar un servidor para que admita servicios de aprendizaje de máquina con SQL Server en estos productos:

+ SQL Server 2016 R Services (In-Database)
+ Servicios de aprendizaje de máquina (en bases de datos) de SQL Server de 2017

> [!NOTE]
> 
> Este contenido se escribió originalmente para la versión de 2016 de SQL Server, que admite solo el lenguaje R.
> 
> En SQL Server 2017, compatibilidad con Python se ha agregado, pero el marco de trabajo de servicios y la arquitectura subyacente es el mismo. Por lo tanto, puede configurar la seguridad, memoria, el regulador de recursos y otras opciones para admitir la ejecución de scripts de Python, del mismo modo que lo haría para scripts de R.
> 
> Sin embargo, dado que la compatibilidad con Python es una característica nueva, la información detallada sobre las posibles optimizaciones para la carga de trabajo de Python todavía no está disponible. Vuelva a comprobarlo más tarde.

## <a name="r-package-management"></a>Administración de paquetes de R

Estos temas describe cómo instalar nuevos paquetes de R en la instancia de SQL Server, administrar las bibliotecas de paquete de R y restaurar las bibliotecas de paquete después de una restauración de base de datos.

+ [Instalar y administrar paquetes de R](installing-and-managing-r-packages.md)
+ [Instalar nuevos paquetes de R](install-additional-r-packages-on-sql-server.md)
+ [Habilitar la administración de paquete para una instancia con Roles de base de datos](r-package-how-to-enable-or-disable.md)
+ [Crear un repositorio de paquete Local mediante miniCRAN](create-a-local-package-repository-using-minicran.md)
+ [Determinar que los paquetes de R instalados en SQl Server](determine-which-packages-are-installed-on-sql-server.md)
+ [Sincronizar los paquetes de R entre SQL Server y el sistema de archivos](package-install-uninstall-and-sync.md)
+ [Paquetes de R instalados en bibliotecas de usuario](packages-installed-in-user-libraries.md)

## <a name="service-configuration"></a>Configuración del servicio

Estos temas describe cómo realizar cambios en la arquitectura subyacente del servicio y cómo administrar a las entidades de seguridad asociadas con el servicio de extensibilidad.

+ [Consideraciones de seguridad](security-considerations-for-the-r-runtime-in-sql-server.md)
+ [Modificar el grupo de cuentas de usuario de SQL Server R Services](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md)
+ [Configuración y administración de Extensiones de análisis avanzados](../../advanced-analytics/r/configure-and-manage-advanced-analytics-extensions.md)
+ [Habilitar la administración de paquete para una instancia con Roles de base de datos](r-package-how-to-enable-or-disable.md)
+ [Optimizar el rendimiento de R Services](sql-server-r-services-performance-tuning.md)

## <a name="resource-governance"></a>Regulación de recursos

Estos temas describe cómo implementar la administración de recursos para los trabajos de R o Python mediante la característica de regulador de recursos que estará disponible en la edición Enterprise.

+ [Regulación de recursos para R Services](../../advanced-analytics/r/resource-governance-for-r-services.md)
+ [Cómo crear un grupo de recursos para R](../../advanced-analytics/r/how-to-create-a-resource-pool-for-r.md)

Vea también:

+ [Uso de informes SSMS personalizado de R de Monitor](monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="initial-setup"></a>Instalación inicial

Encontrará ayuda adicional relacionada con la instalación y configuración iniciales en estos temas:

+ [Preguntas más frecuentes sobre actualización e instalación](../r/upgrade-and-installation-faq-sql-server-r-services.md)
+ [Consideraciones de seguridad](../r/security-considerations-for-the-r-runtime-in-sql-server.md)
+ [Problemas conocidos de R Services](../../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)


