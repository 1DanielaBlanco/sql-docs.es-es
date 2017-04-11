---
title: "Secundarias activas: copia de seguridad en las r&#233;plicas secundarias (grupos de disponibilidad AlwaysOn) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "prioridad de copia de seguridad"
  - "copia de seguridad en réplicas secundarias"
  - "Grupos de disponibilidad [SQL Server], réplicas de disponibilidad"
  - "Grupos de disponibilidad [SQL Server], hacer copia de seguridad en réplicas secundarias"
  - "réplicas secundarias activas [SQL Server], copia de seguridad en"
  - "preferencia de copia de seguridad automatizada"
  - "Grupos de disponibilidad [SQL Server], réplicas secundarias activas"
ms.assetid: 82afe51b-71d1-4d5b-b20a-b57afc002405
caps.latest.revision: 34
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 34
---
# Secundarias activas: copia de seguridad en las r&#233;plicas secundarias (grupos de disponibilidad AlwaysOn)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Las funciones secundarias activas de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] incluyen compatibilidad para realizar operaciones de copia de seguridad en las réplicas secundarias. Las operaciones de copia de seguridad pueden provocar una demanda significativa de E/S y CPU (con la compresión de copia de seguridad). La descarga de las copias de seguridad en una réplica secundaria sincronizada o en proceso de sincronización permite utilizar los recursos de la instancia del servidor que hospeda la réplica principal para las cargas de trabajo de nivel 1.  
  
> [!NOTE]  
>  Las instrucciones RESTORE no se permiten en las bases de datos principales o secundarias de un grupo de disponibilidad.  
  
-   [Tipos de copia de seguridad admitidos](#SupportedBuTypes)  
  
-   [Configurar dónde se ejecutan los trabajos de copia de seguridad](#WhereBuJobsRun)  
  
-   [Tareas relacionadas](#RelatedTasks)  
  
##  <a name="SupportedBuTypes"></a> Tipos de copia de seguridad admitidos en réplicas secundarias  
  
-   **BACKUP DATABASE** solo admite copias de seguridad completas de solo copia de bases de datos, archivos o grupos de archivos cuando se ejecuta en réplicas secundarias. Tenga en cuenta que las copias de seguridad de solo copia no afectan a la cadena de registros ni borran el mapa de bits diferencial.  
  
-   Las copias de seguridad diferenciales no se admiten en las réplicas secundarias.  
  
-   **BACKUP LOG** solo admite copias de seguridad de registros periódicas (la opción COPY_ONLY no se admite para las copias de seguridad de registros en réplicas secundarias).  
  
     Se garantiza una cadena de registro coherente entre las copias de seguridad de registros realizaron en cualquiera de las réplicas (principal o secundaria), con independencia de su modo de disponibilidad (confirmación sincrónica o asincrónica).  
  
-   Para realizar una copia de seguridad de una base de datos secundaria, una réplica secundaria debe poder comunicarse con la réplica principal y su estado debe ser **SYNCHRONIZED** o **SYNCHRONIZING**.  
  
##  <a name="WhereBuJobsRun"></a> Configurar dónde se ejecutan los trabajos de copia de seguridad  
 La realización de copias de seguridad en una réplica secundaria para descargar la carga de trabajo de copias de seguridad del servidor de producción principal es un gran ventaja. Sin embargo, realizar copias de seguridad en réplicas secundarias agrega una gran complejidad al proceso de determinar dónde deben ejecutarse los trabajos de copia de seguridad. Para solucionar este problema, configure dónde se han de ejecutar los trabajos de copia de seguridad del modo siguiente:  
  
1.  Configure el grupo de disponibilidad para que se especifiquen las réplicas de disponibilidad donde preferiría que se realizasen las copias de seguridad. Para obtener más información, vea los parámetros *AUTOMATED_BACKUP_PREFERENCE* y *BACKUP_PRIORITY* en [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/create-availability-group-transact-sql.md) o [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-availability-group-transact-sql.md).  
  
2.  Cree los trabajos de copia de seguridad incluidos en script para cada base de datos de disponibilidad de cada instancia de servidor que hospeda una réplica de disponibilidad que es candidata para realizar copias de seguridad. Para obtener más información, vea la sección "Seguimiento: después de configurar la copia de seguridad en las réplicas secundarias" de [Configurar la copia de seguridad en réplicas de disponibilidad &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Tareas relacionadas  
 **Para configurar la copia de seguridad en las réplicas secundarias**  
  
-   [Configurar la copia de seguridad en réplicas de disponibilidad &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)  
  
 **Para determina sir la réplica actual es la réplica de copia de seguridad preferida**  
  
-   [sys.fn_hadr_backup_is_preferred_replica](../../../relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql.md)  
  
 **Para crear un trabajo de copia de seguridad**  
  
-   [Usar el Asistente para planes de mantenimiento](../../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
-   [Implementar trabajos](../../../ssms/agent/implement-jobs.md)  
  
## Vea también  
 [Información general de los grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Copias de seguridad de solo copia &#40;SQL Server&#41;](../../../relational-databases/backup-restore/copy-only-backups-sql-server.md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  