---
title: "Configurar los valores de la propiedad FailureConditionLevel | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 513dd179-9a46-46da-9fdd-7632cf6d0816
caps.latest.revision: 29
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 29
---
# Configurar los valores de la propiedad FailureConditionLevel
  Use la propiedad FailureConditionLevel para establecer las condiciones para que la instancia de clúster de conmutación por error AlwaysOn (FCI) conmute por error o se reinicie. Los cambios en esta propiedad se aplican inmediatamente sin tener que reiniciar el servicio de Clúster de conmutación por error de Windows Server (WSFC) o el recurso FCI.  
  
-   **Antes de empezar:**  [Valores de propiedad FailureConditionLevel](#Restrictions), [Seguridad](#Security)  
  
-   **Para configurar la propiedad FailureConditionLevel, mediante,** [PowerShell](#PowerShellProcedure), [Administrador de clústeres de conmutación por error](#WSFC), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Antes de empezar  
  
###  <a name="Restrictions"></a> Configuración de la propiedad FailureConditionLevel  
 Las condiciones de error se establecen en una escala creciente. Para los niveles 1 a 5, cada nivel incluye todas las condiciones de los niveles anteriores además de sus propias condiciones. Esto significa que con cada nivel, hay mayor probabilidad de que se produzca una conmutación por error o un reinicio.  Para obtener más información, vea la sección "Determinar los errores" del tema [Failover Policy for Failover Cluster Instances](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md) .  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 Se necesitan los permisos ALTER SETTINGS y VIEW SERVER STATE.  
  
##  <a name="PowerShellProcedure"></a> Usar PowerShell  
  
##### Para configurar los valores de FailureConditionLevel  
  
1.  Inicie Windows PowerShell con derechos elevados mediante **Ejecutar como administrador**.  
  
2.  Importe el módulo **FailoverClusters** para habilitar los cmdlets de clúster.  
  
3.  Use el cmdlet **Get-ClusterResource** con el objetivo de encontrar el recurso de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], después, use el cmdlet **Set-ClusterParameter** a fin de establecer la propiedad **FailureConditionLevel** para una instancia de clúster de conmutación por error.  
  
> [!TIP]  
>  Cada vez que abre una nueva ventana de PowerShell, necesita importar el módulo **FailoverClusters**.  
  
### Ejemplo (PowerShell)  
 En el ejemplo siguiente se cambia el valor de FailureConditionLevel en el recurso "`SQL Server (INST1)`" de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] para la conmutación por error o el reinicio en caso de que se produzcan errores críticos en el servidor.  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter FailureConditionLevel 3  
  
```  
  
### Contenido relacionado (PowerShell)  
  
-   [Clustering and High-Availability (Clústeres y alta disponibilidad)](http://blogs.msdn.com/b/clustering/archive/2009/05/23/9636665.aspx) (blog del equipo de Agrupacion de clústeres de conmutación por error y equilibrio de carga de red)  
  
-   [Introducción a Windows PowerShell en un clúster de conmutación por error](http://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [Comandos de recursos de clúster y cmdlets equivalentes de Windows PowerShell](http://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="WSFC"></a> Usar el complemento Administrador de clústeres de conmutación por error  
 **Para configurar los valores de la propiedad FailureConditionLevel:**  
  
1.  Abra el complemento Administrador de clústeres de conmutación por error.  
  
2.  Expanda **Servicios y aplicaciones** y seleccione la FCI.  
  
3.  Haga clic con el botón derecho en el **recurso de SQL Server** en **Otros recursos** y seleccione **Propiedades** en el menú. Se abrirá el cuadro de diálogo **Propiedades** del recurso de SQL Server.  
  
4.  Seleccione la pestaña **Propiedades** , escriba el valor deseado para la propiedad **FaliureConditionLevel** y, a continuación, haga clic en **Aceptar** para aplicar el cambio.  
  
##  <a name="TsqlProcedure"></a> Usar Transact-SQL  
 **Para configurar los valores de la propiedad FailureConditionLevel:**  
  
 Con la instrucción [ALTER SERVER CONFIGURATION](../../../t-sql/statements/alter-server-configuration-transact-sql.md)[!INCLUDE[tsql](../../../includes/tsql-md.md)] puede especificar el valor de la propiedad FailureConditionLevel.  
  
###  <a name="TsqlExample"></a> Ejemplo (Transact-SQL)  
 En el ejemplo siguiente se establece la propiedad FailureConditionLevel en 0, lo que indica que no se desencadenará automáticamente una conmutación por error o un reinicio si se produce algún error.  
  
```  
ALTER SERVER CONFIGURATION SET FAILOVER CLUSTER PROPERTY FailureConditionLevel = 0;  
```  
  
## Vea también  
 [sp_server_diagnostics &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md)   
 [Directiva de conmutación por error para instancias de clústeres de conmutación por error](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md)  
  
  