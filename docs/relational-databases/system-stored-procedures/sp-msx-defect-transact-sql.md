---
title: sp_msx_defect (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_msx_defect
- sp_msx_defect_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_msx_defect
ms.assetid: 0dfd963a-3bc5-4b58-94f7-aec976da2883
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cf63da8bfb0ac882e3d3949a91b848ba689985a6
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a name="spmsxdefect-transact-sql"></a>sp_msx_defect (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Quita el servidor actual de las operaciones multiservidor.  
  
> [!CAUTION]  
>  **sp_msx_defect** modifica el registro. No se recomienda la modificación manual del Registro porque los cambios inapropiados o incorrectos pueden causar graves problemas de configuración en el sistema. Por tanto, solo los usuarios experimentados deben utilizar el programa Editor del Registro para modificar el Registro. Para obtener más información, consulte la documentación de Microsoft Windows.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_msx_defect [@forced_defection =] forced_defection  
```  
  
## <a name="arguments"></a>Argumentos  
 [ **@forced_defection =**] *forced_defection*  
 Especifica si se debe o no forzar la baja se producen cuando el SQLServerAgent maestro se ha perdido permanentemente debido a daños irreversibles **msdb** base de datos o elija no **msdb** copia de seguridad de base de datos. *forced_defection*es **bits**, su valor predeterminado es **0**, lo que indica que no se debe realizar ningún exigida. Un valor de **1** fuerza la baja.  
  
 Tras forzar una baja mediante la ejecución de **sp_msx_defect**, un miembro de la **sysadmin** rol fijo de servidor en el SQLServerAgent maestro debe ejecutar el comando siguiente para completar la baja:  
  
```  
EXECUTE msdb.dbo.sp_delete_targetserver @server_name = 'tsx-server', @post_defection =  0;  
```  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 None  
  
## <a name="remarks"></a>Comentarios  
 Cuando **sp_msx_defect** finaliza correctamente, se devuelve un mensaje.  
  
## <a name="permissions"></a>Permissions  
 Para ejecutar este procedimiento almacenado, un usuario debe ser miembro del rol fijo de servidor **sysadmin** .  
  
## <a name="see-also"></a>Vea también  
 [sp_msx_enlist &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
