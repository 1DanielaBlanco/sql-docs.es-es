---
title: sp_changearticlecolumndatatype (Transact-SQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_changearticlecolumndatatype
- sp_changearticlecolumndatatype_TSQL
helpviewer_keywords:
- sp_changearticlecolumndatatype
ms.assetid: 0db80e08-fb77-4d0c-aa41-455b13ffa9b4
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 767ef714a2be9a2320ea285b2f389be42309baca
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="spchangearticlecolumndatatype-transact-sql"></a>sp_changearticlecolumndatatype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cambia la asignación del tipo de datos de la columna del artículo en una publicación de Oracle. Este procedimiento almacenado se ejecuta en el distribuidor de cualquier base de datos.  
  
> [!NOTE]  
>  De forma predeterminada, se proporcionan las asignaciones de tipos de datos entre los tipos de publicadores admitidos. Use **sp_changearticlecolumndatatype** solo al reemplazar estos valores predeterminados.  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
sp_changearticlecolumndatatype [ @publication= ] 'publication'  
    [ @article = ] 'article'   
    [ @column = ] 'column'  
    [ , [ @type = ] 'type' ]  
    [ , [ @length = ] length ]  
    [ , [ @precision = ] precision ]  
    [ , [ @scale = ] scale ]  
    [ , [ @publisher = ] 'publisher'  
```  
  
## <a name="arguments"></a>Argumentos  
 [  **@publication=** ] **'***publicación***'**  
 Es el nombre de la publicación de Oracle. *publicación* es **sysname**, no tiene ningún valor predeterminado.  
  
 [  **@article =** ] **'***artículo***'**  
 Es el nombre del artículo. *artículo* es **sysname**, no tiene ningún valor predeterminado.  
  
 [ **@column**=] **'***columna***'**  
 Es el nombre de la columna a la que se va a cambiar la asignación del tipo de datos. *columna* es **sysname**, no tiene ningún valor predeterminado.  
  
 [ **@type** =] **'***tipo***'**  
 Es el nombre de la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tipo de datos en la columna de destino. *tipo de* es **sysname**, su valor predeterminado es null.  
  
 [ **@length** =] *longitud*  
 Es la longitud del tipo de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en la columna de destino. *longitud* es **bigint**, su valor predeterminado es null.  
  
 [ **@precision**=] *precisión*  
 Es la precisión del tipo de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en la columna de destino. *precisión* es **bigint**, su valor predeterminado es null.  
  
 [ **@publisher**=] **'***publisher***'**  
 Especifica un no[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] publisher. *Publisher* es **sysname**, su valor predeterminado es null.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 **0** (correcto) o **1** (error)  
  
## <a name="remarks"></a>Comentarios  
 **Sp_changearticlecolumndatatype** se usa para invalidar las asignaciones de tipo de datos predeterminadas entre tipos de publicadores admitidos (Oracle y [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]). Para ver estas asignaciones de tipos de datos de forma predeterminada, ejecute [sp_getdefaultdatatypemapping](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md).  
  
 **sp_changearticlecolumndatatype** solo se admite para publicadores de Oracle. Ejecutar este procedimiento almacenado contra una publicación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] produce un error.  
  
 **sp_changearticlecolumndatatype** se debe ejecutar para cada asignación de columna del artículo que se debe cambiar.  
  
## <a name="permissions"></a>Permissions  
 Solo los miembros de la **sysadmin** rol fijo de servidor o **db_owner** rol fijo de base de datos puede ejecutar **sp_changearticlecolumndatatype**.  
  
## <a name="see-also"></a>Vea también  
 [Cambiar las propiedades de la publicación y de los artículos](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Data Type Mapping for Oracle Publishers](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [Procedimientos almacenados de replicación &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
