---
title: ALTER HADR de conjunto de base de datos (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET HADR
- SET_HADR_TSQL
- HADR_TSQL
- HADR
dev_langs: TSQL
helpviewer_keywords:
- ALTER DATABASE statement, AlwaysOn Availability Group
- ALTER DATABASE statement, SET HADR options
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], Transact-SQL statements
- Availability Groups [SQL Server], databases
ms.assetid: 20e6e803-d6d5-48d5-b626-d1e0a73d174c
caps.latest.revision: "44"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: a06e868a26e0da160e70e7f2923496e73f136ff7
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="alter-database-transact-sql-set-hadr"></a>SET HADR de ALTER DATABASE (Transact-SQL) 
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Este tema contiene la sintaxis de ALTER DATABASE para establecer [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] opciones en una base de datos secundaria. Se permite solo una opción SET HADR por instrucción ALTER DATABASE. Estas opciones solo se admiten en réplicas secundarias.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
ALTER DATABASE database_name  
   SET HADR   
   {  
        { AVAILABILITY GROUP = group_name | OFF }  
   | { SUSPEND | RESUME }  
   }  
[;]  
```  
  
## <a name="arguments"></a>Argumentos  
 *database_name*  
 Es el nombre de la base de datos secundaria que se va a modificar.  
  
 SET HADR  
 Ejecuta el comando de [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] especificado en la base de datos indicada.  
  
 {El grupo de disponibilidad  **=**  *nombre_grupo* | {OFF}  
 Une o quita la base de datos de disponibilidad del grupo de disponibilidad especificado, de la manera siguiente:  
  
 *nombre_grupo*  
 Une la base de datos especificada de la réplica secundaria hospedada por la instancia del servidor en la que se ejecuta el comando al grupo de disponibilidad especificado por group_name.  
  
 Los requisitos previos para esta operación son los siguientes:  
  
-   La base de datos debe haberse agregado al grupo de disponibilidad de la réplica principal.  
  
-   La réplica principal debe estar activa. Para obtener información acerca de cómo solucionar problemas de una réplica principal inactiva, consulte [solución de problemas siempre en grupos de configuración de disponibilidad (SQL Server)](http://go.microsoft.com/fwlink/?LinkId=225834).  
  
-   La réplica principal debe estar en línea y la réplica secundaria debe estar conectada a la réplica principal.  
  
-   La base de datos secundaria debe haberse restaurado mediante WITH NORECOVERY desde las copias de seguridad recientes de bases de datos y de registros de la base de datos principal, finalizando con una copia de seguridad de registros que sea suficientemente reciente como para permitir que la base de datos secundaria se ponga al día con la base de datos principal.  
  
    > [!NOTE]  
    >  Para agregar una base de datos al grupo de disponibilidad, conéctese a la instancia de servidor que hospeda la réplica principal y use la [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md)*nombre_grupo* Agregar base de datos *database_name*  instrucción.  
  
 Para obtener más información, vea [Combinar una base de datos secundaria con un grupo de disponibilidad &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/join-a-secondary-database-to-an-availability-group-sql-server.md).  
  
 OFF  
 Quita la base de datos secundaria especificada del grupo de disponibilidad.  
  
 Quitar una base de datos secundaria puede ser útil si se ha retrasado con respecto a la base de datos principal y no desea esperar hasta que la base de datos secundaria se ponga al día. Después de quitar la base de datos secundaria, se puede actualizar mediante la restauración de una secuencia de copias de seguridad que terminan con una copia de seguridad de registros reciente (mediante RESTORE … CON LA OPCIÓN NORECOVERY).  
  
> [!IMPORTANT]  
>  Para quitar completamente una base de datos de disponibilidad de un grupo de disponibilidad, conéctese a la instancia del servidor que hospeda la réplica principal y use la [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md)*nombre_grupo* quitar Base de datos *availability_database_name* instrucción. Para obtener más información, vea [quitar una base de datos principal de un grupo de disponibilidad &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/remove-a-primary-database-from-an-availability-group-sql-server.md).  
  
 SUSPEND  
 Suspende el movimiento de datos en una base de datos secundaria. Un comando SUSPEND realiza la devolución en cuanto haya sido aceptado por la réplica que hospeda la base de datos de destino, pero la suspensión real de la base de datos se produce de forma asincrónica.  
  
 El ámbito del impacto depende de dónde se ejecute la instrucción ALTER DATABASE:  
  
-   Si suspende una base de datos secundaria en una réplica secundaria, solo se suspende la base de datos secundaria local. Las conexiones existentes en la secundaria legible siguen estando utilizables. Las nuevas conexiones a la base de datos suspendida en la secundaria legible no se permiten hasta que se reanude el movimiento de datos.  
  
-   Si suspende una base de datos en la réplica principal, el movimiento de datos se suspende en las bases de datos secundarias correspondientes en cada réplica secundaria. Las conexiones existentes en una base de datos secundaria legible permanecen utilizables y nuevas conexiones de intención de lectura no podrá conectarse a réplicas secundarias legibles.  
  
-   Cuando se suspende el movimiento de datos debido a una conmutación por error manual forzada, no se permiten las conexiones a la nueva réplica secundaria mientras el movimiento de datos esté suspendido.  
  
 Cuando se suspende una base de datos en una réplica secundaria, tanto la base de datos como la réplica quedan desincronizadas y se marcan como NOT SYNCHRONIZED.  
  
> [!IMPORTANT]  
>  Mientras se suspende una base de datos secundaria, la cola de envío de la base de datos principal correspondiente acumulará registros de transacciones sin enviar. Las conexiones a la réplica secundaria devuelven los datos que estaban disponibles en el momento en que suspendió el movimiento de datos.  
  
> [!NOTE]  
>  Suspender y reanudar un siempre en base de datos secundaria no afecta directamente a la disponibilidad de la base de datos principal, aunque suspender una base de datos secundaria puede afectar a las capacidades de conmutación por error y redundancia para la base de datos principal, hasta que la suspensión se reanuda la base de datos secundaria. Esto se diferencia del reflejo de base de datos, en el que el estado de reflejo se suspende tanto en la base de datos reflejada como en la base de datos principal hasta que el reflejo se reanuda. Al suspender una base de datos principal AlwaysOn, se suspende el movimiento de datos en todas las bases de datos secundarias y las capacidades de conmutación por error y redundancia cesan para esa base de datos hasta que la base de datos principal se reanuda.  
  
 Para obtener más información, vea [suspender una base de datos de disponibilidad &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/suspend-an-availability-database-sql-server.md).  
  
 RESUME  
 Reanuda el movimiento de datos suspendido en la base de datos secundaria especificada. Un comando RESUME realiza la devolución en cuanto haya sido aceptado por la réplica que hospeda la base de datos de destino, pero la reanudación real de la base de datos se produce de forma asincrónica.  
  
 El ámbito del impacto depende de dónde se ejecute la instrucción ALTER DATABASE:  
  
-   Si reanuda una base de datos secundaria en una réplica secundaria, solo se reanuda la base de datos secundaria local. El movimiento de datos se reanuda a menos que la base de datos también se haya suspendido en la réplica principal.  
  
-   Si reanuda una base de datos en la réplica principal, el movimiento de datos se reanuda en cada réplica secundaria en la que la base de datos secundaria correspondiente tampoco se haya suspendido localmente. Para reanudar una base de datos secundaria que se suspendió individualmente en una réplica secundaria, conéctese a la instancia del servidor que hospeda la réplica secundaria y reanude la base de datos allí.  
  
     En el modo de confirmación sincrónica, el estado de la base de datos cambia a SYNCHRONIZING. Si no hay ninguna otra base de datos suspendida actualmente, el estado de la réplica también cambia a SYNCHRONIZING.  
  
     Para obtener más información, vea [Reanudar una base de datos de disponibilidad &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/resume-an-availability-database-sql-server.md).  
  
## <a name="database-states"></a>Estados de base de datos  
 Cuando una base de datos secundaria se une a un grupo de disponibilidad, la réplica secundaria local cambia el estado de la base de datos secundaria de RESTORING a ONLINE. Si se quita una base de datos secundaria del grupo de disponibilidad, la réplica secundaria local vuelve a establecerse al estado RESTORING. Esto permite aplicar copias de seguridad de registros subsiguientes de la base de datos principal a la base de datos secundaria.  
  
## <a name="restrictions"></a>Restricciones  
 Ejecute las instrucciones ALTER DATABASE fuera de transacciones y de lotes.  
  
## <a name="security"></a>Seguridad  
  
### <a name="permissions"></a>Permisos  
 Requiere el permiso ALTER en la base de datos. Combinar una base de datos a un grupo de disponibilidad requiere ser miembro de la **db_owner** rol fijo de base de datos.  
  
## <a name="examples"></a>Ejemplos  
 En el ejemplo siguiente se une la base de datos secundaria `AccountsDb1` a la réplica secundaria local del grupo de disponibilidad `AccountsAG`.  
  
```  
ALTER DATABASE AccountsDb1 SET HADR AVAILABILITY GROUP = AccountsAG;  
```  
  
> [!NOTE]  
>  Para ver esta instrucción [!INCLUDE[tsql](../../includes/tsql-md.md)] usada en contexto, vea [Crear un grupo de disponibilidad &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md).  
  
## <a name="see-also"></a>Vea también  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [Información general de grupos de disponibilidad AlwaysOn &#40; SQL Server &#41; ](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) [Solucionar problemas de configuración de grupos de disponibilidad AlwaysOn &#40; SQL Server &#41;](../../database-engine/availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md) 
  
  
