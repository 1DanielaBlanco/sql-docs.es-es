---
title: sp_set_firewall_rule (base de datos de SQL Azure) | Documentos de Microsoft
ms.custom: 
ms.date: 07/28/2016
ms.prod: 
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: 
ms.service: sql-database
ms.component: system-stored-procedures
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_set_firewall_rule
- sp_set_firewall_rule_TSQL
- sys.sp_set_firewall_rule
- sys.sp_set_firewall_rule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_set_firewall_rule
- firewall_rules, setting server rules
ms.assetid: a974a561-5382-4039-8499-3a56767bcefe
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 38ef5788aba91bfde21df091321a69dbacbeb8e9
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="spsetfirewallrule-azure-sql-database"></a>sp_set_firewall_rule (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  Crea o actualiza la configuración del firewall de nivel de servidor para el servidor [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Este procedimiento almacenado solo está disponible en la base de datos maestra para el inicio de sesión principal de nivel de servidor o la entidad de seguridad de Azure Active Directory asignado.  
  
  
## <a name="syntax"></a>Sintaxis  
  
```
sp_set_firewall_rule [@name =] 'name', 
    [@start_ip_address =] 'start_ip_address', 
    [@end_ip_address =] 'end_ip_address'
[ ; ]  
```  
  
## <a name="arguments"></a>Argumentos  
 En la tabla siguiente se muestran los argumentos compatibles y opciones en [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
|Nombre|Datatype|Description|  
|----------|--------------|-----------------|  
|[@name =] 'name'|**NVARCHAR (128)**|El nombre utilizado para describir y distinguir la configuración del firewall de nivel de servidor.|  
|[@start_ip_address =] 'start_ip_address'|**VARCHAR (50)**|La dirección IP más baja en el intervalo de la configuración del firewall de nivel de servidor. Las direcciones IP iguales o superiores a esta pueden intentar conectarse con el servidor [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. La dirección IP más baja posible es `0.0.0.0`.|  
|[@end_ip_address =] 'end_ip_address'|**VARCHAR (50)**|La dirección IP más alta en el intervalo de la configuración del firewall de nivel de servidor. Las direcciones IP iguales o inferiores a esta pueden intentar conectarse con el servidor [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. La dirección IP más alta posible es `255.255.255.255`.<br /><br /> Nota: Los intentos de conexión de Azure se permiten cuando este campo y el *start_ip_address* campo es igual a `0.0.0.0`.|  
  
## <a name="remarks"></a>Comentarios  
 Los nombres de la configuración del firewall de nivel de servidor deben ser únicos. Si el nombre del valor proporcionado para el procedimiento almacenado ya existe en la tabla de configuración del firewall, las direcciones IP inicial y final se actualizarán. De lo contrario, se creará una nueva configuración del firewall de nivel de servidor.  
  
 Cuando se agrega una configuración de firewall de nivel de servidor donde el principio y final de las direcciones IP son iguales a `0.0.0.0`, habilite el acceso a su [!INCLUDE[ssSDS](../../includes/sssds-md.md)] servidor de Azure. Proporcione un valor para el *nombre* parámetro que le ayudará a recordar qué es la configuración de firewall de nivel de servidor.  
  
 En [!INCLUDE[ssSDS](../../includes/sssds-md.md)], datos de inicio de sesión necesitan para autenticar una conexión y las reglas de firewall de nivel de servidor se almacenan temporalmente en caché en cada base de datos. Esta caché se actualiza periódicamente. Para forzar una actualización de la caché de autenticación y asegúrese de que una base de datos tiene la versión más reciente de la tabla de inicios de sesión, ejecute [DBCC FLUSHAUTHCACHE &#40; Transact-SQL &#41; ](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Solo el nivel de servidor de inicio de sesión principal creado por el proceso de aprovisionamiento o una entidad de seguridad de Azure Active Directory asignado como administrador puede crear o modificar reglas de firewall de nivel de servidor. El usuario debe estar conectado a la base de datos maestra para ejecutar sp_set_firewall_rule.  
  
## <a name="examples"></a>Ejemplos  
 El siguiente código crea un firewall de nivel de servidor llamada `Allow Azure` que habilita el acceso de Azure. Ejecute lo siguiente en la base de datos maestra virtual.  
  
```  
-- Enable Windows Azure connections.  
exec sp_set_firewall_rule N'Allow Azure', '0.0.0.0', '0.0.0.0';  
  
```  
  
 El código siguiente crea una configuración del firewall de nivel de servidor denominada `Example setting 1` solo para la dirección IP `0.0.0.2`. A continuación, la `sp_set_firewall_rule` procedimiento almacenado se llama de nuevo para actualizar la dirección IP final `0.0.0.4`, ya que la configuración de firewall. Esto crea un intervalo que permite que las direcciones IP `0.0.0.2`, `0.0.0.3`, y `0.0.0.4` para tener acceso al servidor.  
  
```  
-- Create server-level firewall setting for only IP 0.0.0.2  
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.2';  
  
-- Update server-level firewall setting to create a range of allowed IP addresses
exec sp_set_firewall_rule N'Example setting 1', '0.0.0.2', '0.0.0.4';  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Firewall de base de datos SQL Azure](https://azure.microsoft.com/documentation/articles/sql-database-firewall-configure/)   
 [Cómo: configurar el Firewall (base de datos SQL Azure)](https://azure.microsoft.com/documentation/articles/sql-database-configure-firewall-settings/)   
 [Sys.firewall_rules &#40; Base de datos SQL Azure &#41;](../../relational-databases/system-catalog-views/sys-firewall-rules-azure-sql-database.md)
