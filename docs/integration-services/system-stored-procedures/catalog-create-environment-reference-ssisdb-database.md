---
title: catalog.create_environment_reference (base de datos de SSISDB) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 48069bea-31cb-4a0e-9849-a07edc94088f
caps.latest.revision: "19"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 22f4ff117ea95ffa394afcd230348c4ab0f525d1
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2017
---
# <a name="catalogcreateenvironmentreference-ssisdb-database"></a>catalog.create_environment_reference (base de datos de SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Crea una referencia de entorno para un proyecto en el catálogo de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```sql  
catalog.create_environment_reference [ @folder_name = ] folder_name  
     , [ @project_name = ] project_name  
     , [ @environment_name = ] environment_name  
     , [ @reference_location = ] reference_location  
  [  , [ @environment_folder_name = ] environment_folder_name ]  
  [  , [ @reference_id = ] reference_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [ @folder_name = ] *folder_name*  
 El nombre de la carpeta del proyecto al que se hace referencia en el entorno. El parámetro *folder_name* es **nvarchar(128)**.  
  
 [ @project_name = ] *project_name*  
 El nombre del proyecto al que se hace referencia en el entorno. El parámetro *project_name* es **nvarchar(128)**.  
  
 [ @environment_name = ] *environment_name*  
 El nombre del entorno al que se hace referencia. El parámetro *environment_name* es **nvarchar(128)**.  
  
 [ @reference_location = ] *reference_location*  
 Indica si el entorno se puede encontrar en la misma carpeta que el proyecto (referencia relativa) o en una carpeta diferente (referencia absoluta). Utilice el valor `R` para indicar una referencia relativa. Utilice el valor `A` para indicar una referencia absoluta. El parámetro *reference_location* es **char(1)**.  
  
 [ @environment_folder_name = ] *environment_folder_name*  
 El nombre de la carpeta en la que se encuentra el entorno al que se hace referencia. Este valor se requiere para las referencias absolutas. El parámetro *environment_folder_name* es **nvarchar(128)**.  
  
 [ @reference_id = ] *reference_id*  
 Devuelve el identificador único para la nueva referencia. Este parámetro es opcional. El parámetro *reference_id* es **bigint**.  
  
## <a name="return-code-value"></a>Valor de código de retorno  
 0 (Correcto)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 Ninguno  
  
## <a name="permissions"></a>Permissions  
 Este procedimiento almacenado necesita uno de los permisos siguientes:  
  
-   Los permisos de lectura y modificación en el proyecto, y el permiso de lectura en el entorno  
  
-   Pertenencia al rol de base de datos de **ssis_admin**  
  
-   Pertenencia al rol de servidor de **sysadmin**  
  
## <a name="errors-and-warnings"></a>Errores y advertencias  
 En la siguiente lista se describen algunas condiciones que pueden producir un error o una advertencia:  
  
-   El nombre de la carpeta no es válido  
  
-   El nombre de proyecto no es válido  
  
-   El usuario no tiene los permisos apropiados  
  
-   Una referencia absoluta se especifica mediante el carácter `A` en el parámetro *reference_location*, pero el nombre de la carpeta no se especificó con el parámetro *environment_folder_name*.  
  
## <a name="remarks"></a>Comentarios  
 Un proyecto puede tener referencias de entorno absolutas o relativas. Las referencias relativas se refieren al entorno por nombre y requieren que resida en la misma carpeta que el proyecto. Las referencias absolutas hacen referencia al entorno por nombre y carpeta, y pueden hacer referencia a los entornos que residen en una carpeta diferente que el proyecto. Un proyecto puede hacer referencia a varios entornos.  
  
  
