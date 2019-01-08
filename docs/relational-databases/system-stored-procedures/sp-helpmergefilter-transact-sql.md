---
title: sp_helpmergefilter (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergefilter
- sp_helpmergefilter_TSQL
helpviewer_keywords:
- sp_helpmergefilter
ms.assetid: f133a094-0009-4771-b93b-e86a5c01e40b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3785eb45e8ecca7a573f499d8c48b184a22e6efc
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2018
ms.locfileid: "52779367"
---
# <a name="sphelpmergefilter-transact-sql"></a>sp_helpmergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Devuelve información acerca de los filtros de mezcla. Este procedimiento almacenado se ejecuta en el publicador de cualquier base de datos.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_helpmergefilter [ @publication= ] 'publication'   
    [ , [ @article= ] 'article']  
    [ , [ @filtername= ] 'filtername']  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@publication=**] **'***publicación***'**  
 Es el nombre de la publicación. *publicación* es **sysname**, no tiene ningún valor predeterminado.  
  
 [  **@article=**] **'***artículo***'**  
 Es el nombre del artículo. *artículo* es **sysname**, su valor predeterminado es **%**, que devuelve los nombres de todos los artículos.  
  
 [  **@filtername=**] **'***filtername***'**  
 Es el nombre del filtro cuya información se va a devolver. *filtername* es **sysname**, su valor predeterminado es **%**, que devuelve información acerca de todos los filtros definidos en el artículo o la publicación.  
  
## <a name="result-sets"></a>Conjuntos de resultados  
  
|Nombre de columna|Tipo de datos|Descripción|  
|-----------------|---------------|-----------------|  
|**join_filterid**|**int**|Id. del filtro de combinación.|  
|**filtername**|**sysname**|Nombre del filtro.|  
|**nombre de artículo de combinación**|**sysname**|Nombre del artículo de combinación.|  
|**join_filterclause**|**nvarchar(2000)**|Cláusula de filtro que califica la combinación.|  
|**join_unique_key**|**int**|Indica si la combinación se hace sobre una clave exclusiva.|  
|**propietario de la tabla base**|**sysname**|Nombre del propietario de la tabla base.|  
|**nombre de la tabla base**|**sysname**|Nombre de la tabla base.|  
|**propietario de la tabla de combinación**|**sysname**|Nombre del propietario de la tabla que se combina con la tabla base.|  
|**nombre de tabla combinada**|**sysname**|Nombre de la tabla que se combina con la tabla base.|  
|**nombre de artículo**|**sysname**|Nombre del artículo de la tabla que se combina con la tabla base.|  
|**filter_type**|**tinyint**|Tipo de filtro de mezcla, que puede ser uno de los siguientes:<br /><br /> **1** = solo filtro de combinación<br /><br /> **2** = relación de registros lógicos<br /><br /> **3** = both|  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **sp_helpmergefilter** se utiliza en la replicación de mezcla.  
  
## <a name="permissions"></a>Permisos  
 Solo los miembros de la **sysadmin** rol fijo de servidor y el **db_owner** rol fijo de base de datos se puede ejecutar **sp_helpmergefilter**.  
  
## <a name="see-also"></a>Vea también  
 [sp_addmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_changemergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_dropmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [Procedimientos almacenados del sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
