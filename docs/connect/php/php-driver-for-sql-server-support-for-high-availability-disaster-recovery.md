---
title: Compatibilidad con alta disponibilidad, recuperación ante desastres para los controladores de Microsoft para PHP para SQL Server | Documentos de Microsoft
ms.custom: ''
ms.date: 04/04/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73a80821-d345-4fea-b076-f4aabeb4af3e
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9d7faa964558281c21b3a5ee92736d26d8def56a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="support-for-high-availability-disaster-recovery"></a>Compatibilidad con recuperación ante desastres de alta disponibilidad
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Este tema se describen [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] compatibilidad del (agregada en la versión 3.0) alta disponibilidad y recuperación ante desastres-- [!INCLUDE[ssHADR](../../includes/sshadr_md.md)].  Se agregó compatibilidad para [!INCLUDE[ssHADR](../../includes/sshadr_md.md)] en [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]. Para obtener más información acerca de [!INCLUDE[ssHADR](../../includes/sshadr_md.md)], vea los Libros en pantalla de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
En la versión 3.0 de la [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], puede especificar el agente de escucha del grupo de disponibilidad de una (alta disponibilidad y recuperación ante desastres) grupo de disponibilidad (AG) en la propiedad de conexión. Si un [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] aplicación está conectada a una base de datos de AlwaysOn que conmuta por error, se pierde la conexión original y la aplicación debe abrir una conexión nueva para seguir trabajando después de la conmutación por error.  
  
Si no se está conectando a un agente de escucha del grupo de disponibilidad y si hay varias direcciones IP asociadas con un nombre de host, el [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] iterará secuencialmente todas las direcciones IP asociadas a entrada DNS. Esto puede llevar mucho tiempo si la primera dirección IP que devuelve el servidor DNS no está enlazada a una tarjeta (NIC) de interfaz de red. Cuando se conecta a un agente de escucha del grupo de disponibilidad, el [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] intenta establecer conexiones a todas las direcciones IP en paralelo, y si un intento de conexión se realiza correctamente, el controlador descartará los demás intentos de conexión pendientes.  
  
> [!NOTE]  
> El aumento del tiempo de espera de la conexión y la implementación de la lógica de reintento de conexión aumentarán la probabilidad de que una aplicación se conecte a un grupo de disponibilidad. Además, dado que una conexión puede producir un error debido a la conmutación por error de un grupo de disponibilidad, es aconsejable implementar la lógica de reintento de conexión y hacer que una conexión que no se ha podido establecer se reintente hasta que vuelva a conectarse.  
  
## <a name="connecting-with-multisubnetfailover"></a>Conectarse a MultiSubnetFailover  
El **MultiSubnetFailover** propiedad de conexión indica que la aplicación se implementa en un grupo de disponibilidad o instancia de clúster de conmutación por error y que la [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] intentará conectarse a la base de datos en el servidor principal [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] direcciones de la instancia intenta conectarse a todas las direcciones IP. Cuando **MultiSubnetFailover = true** se especifica para una conexión, el cliente lo reintenta intentos de conexión TCP más rápidamente que los intervalos de retransmisión TCP del sistema operativo de forma predeterminada. Esto permite una reconexión más rápida después de la conmutación por error de un grupo de disponibilidad AlwaysOn o una instancia de clúster de conmutación por error AlwaysOn, y es aplicable a instancias de clúster de conmutación por error y grupos de disponibilidad de una y varias subredes.  
  
Especifique siempre **MultiSubnetFailover = True** al conectarse a un agente de escucha del grupo de disponibilidad de SQL Server 2012 o una instancia de clúster de conmutación por error de SQL Server 2012. **MultiSubnetFailover** habilita más rápida conmutación por error para todos los grupos de disponibilidad y una instancia de clúster de conmutación por error de SQL Server 2012 y reduce considerablemente el tiempo de conmutación por error para las topologías de AlwaysOn y de varias subredes. En un clúster de conmutación por error de varias subredes, el cliente intentará conexiones en paralelo. Durante una conmutación por error de subred, el [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] seguirá Reintentando la conexión TCP.  
  
Para obtener más información sobre las palabras clave de cadena de conexión en [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], consulte [opciones de conexión](../../connect/php/connection-options.md).  
  
Especificar **MultiSubnetFailover = true** al conectarse a algo distinto de un agente de escucha del grupo de disponibilidad o una instancia de clúster de conmutación por error puede producir un impacto negativo en el rendimiento y no se admite.  
  
Utilice las siguientes instrucciones para conectarse a un servidor de un grupo de disponibilidad :  
  
-   Use la propiedad de conexión **MultiSubnetFailover** cuando se conecte a una única subred o a varias subredes, ya que mejorará el rendimiento en ambos casos.  
  
-   Para conectarse a un grupo de disponibilidad, especifique el agente de escucha del grupo de disponibilidad como el servidor en la cadena de conexión.  
  
-   La conexión a una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] configurada con más de 64 direcciones IP producirá un error en la conexión.  
  
-   El comportamiento de una aplicación que usa la propiedad de conexión **MultiSubnetFailover** no se ve afectado por el tipo de autenticación: autenticación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], autenticación Kerberos o autenticación de Windows.  
  
-   Aumente el valor de **loginTimeout** para dar tiempo de conmutación por error y reducir los reintentos de conexión de aplicación.  
  
-   No se admiten las transacciones distribuidas.  
  
Si no está activado el enrutamiento de solo lectura, no se podrá conectar a una ubicación de réplica secundaria en un grupo de disponibilidad en las siguientes situaciones:  
  
1.  Si la ubicación de réplica secundaria no está configurada para aceptar conexiones.  
  
2.  Si una aplicación usa **ApplicationIntent=ReadWrite** (se describe a continuación) y la ubicación de réplica secundaria está configurada para acceso de solo lectura.  
  
Una conexión producirá un error si una réplica principal está configurada para rechazar cargas de trabajo de solo lectura y la cadena de conexión contiene **ApplicationIntent=ReadOnly**.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Actualizar para utilizar clústeres de varias subredes a partir de la creación de reflejo de la base de datos  
Se producirá un error de conexión si las palabras clave de conexión **MultiSubnetFailover** y **Failover_Partner** se encuentran en la cadena de conexión. También se producirá un error si se usa **MultiSubnetFailover** y [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] devuelve una respuesta del asociado de conmutación por error que indica que forma parte de un par de creación de reflejo de la base de datos.  
  
Si actualiza un [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] aplicación que emplea actualmente creación de reflejo de base de datos a un escenario de múltiples subredes, debe quitar la **Failover_Partner** propiedad de conexión y reemplazarla con **MultiSubnetFailover**  establecido en **Sí** y reemplace el nombre del servidor en la cadena de conexión con un agente de escucha del grupo de disponibilidad. Si usa una cadena de conexión **Failover_Partner** y **MultiSubnetFailover = true**, el controlador generará un error. Sin embargo, si usa una cadena de conexión **Failover_Partner** y **MultiSubnetFailover = false** (o **ApplicationIntent = ReadWrite**), la aplicación utilizará la base de datos creación de reflejo.  
  
El controlador devolverá un error si la creación de reflejo de base de datos se utiliza en la base de datos principal en el AG y si **MultiSubnetFailover = true** se utiliza en la cadena de conexión que se conecta a una base de datos principal en lugar de un grupo de disponibilidad agente de escucha.  


[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]


## <a name="see-also"></a>Vea también  
[Conexión al servidor](../../connect/php/connecting-to-the-server.md)  
  
