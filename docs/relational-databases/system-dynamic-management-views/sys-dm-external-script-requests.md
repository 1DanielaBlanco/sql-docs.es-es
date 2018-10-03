---
title: Sys.dm_external_script_requests | Microsoft Docs
ms.custom: ''
ms.date: 06/24/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_external_script_requests
- sys.dm_external_script_requests_TSQL
- dm_external_script_requests
- dm_external_script_requests_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_external_script_requests dynamic management view
ms.assetid: e7e7c50f-b8b2-403c-b8c8-1955da5636c3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fb5597a9163ac87e9f6c08421025340cf8263b44
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47843473"
---
# <a name="sysdmexternalscriptrequests"></a>sys.dm_external_script_requests
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Devuelve una fila para cada cuenta de trabajo activa que ejecuta un script externo.
 
  
> [!NOTE] 
>  
>  Esta DMV solo está disponible si ha instalado y después habilitado la característica que admite la ejecución del script externo. Para más información sobre cómo hacer esto para scripts de R, consulte [Set Up SQL Server R Services](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md) (Configuración de servicios de R de SQL Server).  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|external_script_request_id|**Identificador único**|Identificador del proceso que envió la solicitud de script externo. Esto corresponde al identificador de proceso, tal como lo recibe [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]|  
|language|**nvarchar**|Palabra clave que representa un lenguaje de script compatible. Actualmente solo e admite `R` .|  
|degree_of_parallelism|**int**|Número que indica el número de procesos paralelos que se crearon. Este valor podría ser diferente del número de procesos paralelos que se solicitaron.|  
|external_user_name|**nvarchar**|La cuenta de trabajo de Windows bajo la que se ejecutó el script.|  
  
## <a name="permissions"></a>Permisos  
 Requiere el permiso VIEW SERVER STATE en el servidor.  
  
> [!NOTE]
>   
>  Los usuarios que ejecuten scripts externos deben tener el permiso adicional EXECUTE ANY EXTERNAL SCRIPT, sin embargo, los administradores pueden usar esta DMV sin este permiso. 
  
## <a name="remarks"></a>Comentarios  

Esta vista se puede filtrar usando el identificador del lenguaje de script.

La vista también devuelve la cuenta de trabajo en la que se ejecuta el script. Para obtener información sobre las cuentas de trabajo que usan los scripts de R, consulte [Modify the User Account Pool for R Services](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md) (Modificar el grupo de cuentas de usuario de servicios de R).

El GUID que se devuelve en el campo **external_script_request_id** también representa el nombre de archivo del directorio seguro donde se almacenan los archivos temporales. Cada cuenta de trabajo como MSSQLSERVER01 representa un único inicio de sesión SQL o usuario de Windows y podría utilizarse para ejecutar varias solicitudes de script. De forma predeterminada, estos archivos temporales se limpian tras la finalización del script. Si necesita conservar estos archivos durante un período determinado para fines de depuración, puede cambiar el indicador de limpieza como se describe en este tema: [Configure and Manage Advanced Analytics Extensions](../../advanced-analytics/r-services/configure-and-manage-advanced-analytics-extensions.md) (Configuración y administración de Extensiones de análisis avanzado).  
 
Esta DMV supervisa solo los procesos activos y no puede informar sobre scripts que ya han completado. Si necesita realizar un seguimiento de la duración de scripts, es recomendable agregar información de tiempo en el script y capturar eso como parte de la ejecución del script.


## <a name="examples"></a>Ejemplos  
  
### <a name="viewing-the-currently-active-r-scripts-for-a-particular-process"></a>Visualización de los scripts de R actualmente activos para un proceso determinado 
 En el ejemplo siguiente se muestra el número de ejecuciones de scripts externos que tienen lugar en la instancia actual.  
  
```  
SELECT external_script_request_id 
  , [language]
  , degree_of_parallelism
  , external_user_name
FROM sys.dm_external_script_requests; 
```  

Resultado  


external_script_request_id  |language  |degree_of_parallelism  |external_user_name  
---------|---------|---------|---------
183EE6FC-7399-4318-AA2E-7A6C68E435A8     |     R    |      1   |  MSSQLSERVER01       


  
## <a name="see-also"></a>Vea también  
 [Funciones y vistas de administración dinámica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Funciones y vistas de administración dinámica relacionadas con ejecuciones &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)
[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
  

