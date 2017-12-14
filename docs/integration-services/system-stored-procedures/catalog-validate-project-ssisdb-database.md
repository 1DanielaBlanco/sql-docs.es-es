---
title: catalog.validate_project (base de datos de SSISDB) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 5270689a-46d4-4847-b41f-3bed1899e955
caps.latest.revision: "13"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 837a052abb35ae767d313b2dd4241d79d2af6074
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2017
---
# <a name="catalogvalidateproject-ssisdb-database"></a>catalog.validate_project (base de datos de SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Valida de forma asincrónica un proyecto del catálogo de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```sql
catalog.validate_project [ @folder_name = ] folder_name  
    , [ @project_name = ] project_name  
    , [ @validate_type = ] validate_type  
    , [ @validation_id = ] validation_id OUTPUT  
 [  , [ @use32bitruntime = ] use32bitruntime ]  
 [  , [ @target_environment = ] target_environment ]  
 [  , [ @reference_id = ] reference_id ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [ @folder_name = ] *folder_name*  
 Nombre de una carpeta que contiene el proyecto. El parámetro *folder_name* es **nvarchar(128)**.  
  
 [ @project_name = ] *project_name*  
 Nombre del proyecto. El parámetro *project_name* es **nvarchar(128)**.  
  
 [ @validate_type = ] *validate_type*  
 Indica el tipo de validación que se llevará a cabo. Utilice el carácter `F` para realizar una validación completa. El parámetro *validate_type* es **char(1)**.  
  
 [ @validation_id = ] *validation_id*  
 Devuelve el identificador único (ID) de la validación. El parámetro *validation_id* es **bigint**.  
  
 [ @use32bitruntime = ] *use32bitruntime*  
 Indica si el motor en tiempo de ejecución de 32 bits se debe usar para ejecutar el paquete en un sistema operativo de 64 bits. Use el valor de `1` para ejecutar el paquete con el entorno de ejecución de 32 bits cuando se ejecute en un sistema operativo de 64 bits. Use el valor `0` para ejecutar el paquete con el motor en tiempo de ejecución de 64 bits cuando se ejecute en un sistema operativo de 64 bits. Este parámetro es opcional. El parámetro *use32bitruntime* es **bit**.  
  
 [ @environment_scope = ] *environment_scope*  
 Indica las referencias de entorno que la validación tiene en cuenta. Cuando el valor es `A`, todas las referencias de entorno asociadas con el proyecto se incluyen en la validación. Cuando el valor es `S`, solo se incluye una sola referencia de entorno. Cuando el valor es `D`, no se incluyen referencias de entorno y todos los parámetros deben tener un valor literal predeterminado para pasar la validación. Este parámetro es opcional, el carácter `D` se usará de forma predeterminada. El parámetro *environment_scope* es **Char(1)**.  
  
 [ @reference_id = ] *reference_id*  
 El identificador único de la referencia de entorno. Este parámetro es obligatorio solo cuando se incluye una sola referencia de entorno en la validación, cuando el parámetro *environment_scope* es `S`. El parámetro *reference_id* es **bigint**.  
  
## <a name="return-code-values"></a>Valores de código de retorno  
 0 (Correcto)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 La salida de los pasos de la validación se devuelve como secciones diferentes del conjunto de resultados.  
  
## <a name="permissions"></a>Permissions  
 Este procedimiento almacenado necesita uno de los permisos siguientes:  
  
-   Permisos de lectura en el objeto y, si es aplicable, permisos de lectura en los entornos a los que se hace referencia  
  
-   Pertenencia al rol de base de datos de **ssis_admin**  
  
-   Pertenencia al rol de servidor de **sysadmin**  
  
## <a name="errors-and-warnings"></a>Errores y advertencias  
 En la siguiente lista se proporcionan algunas condiciones que pueden producir un error o una advertencia:  
  
-   La validación no puede realizarse para uno o más paquetes del proyecto  
  
-   La validación no puede realizarse si uno o varios de los entornos a los que se hace referencia y que están incluidos en la validación no contienen variables a las que se haga referencia  
  
-   El tipo de validación especificado no es válido  
  
-   El nombre del proyecto o el identificador de la referencia del entorno es no válido  
  
-   El usuario no tiene los permisos adecuados  
  
## <a name="remarks"></a>Comentarios  
 La validación ayuda a identificar problemas que impedirán que los paquetes del proyecto se ejecuten correctamente. Use las vistas [catalog.validations](../../integration-services/system-views/catalog-validations-ssisdb-database.md) o [catalog.operations](../../integration-services/system-views/catalog-operations-ssisdb-database.md) para supervisar el estado de validación.  
  
 Solo los entornos que son accesibles por el usuario se pueden utilizar en la validación. El resultado de la validación se envía al cliente como un conjunto de resultados.  
  
 En esta versión, la validación del proyecto no admite la validación de dependencias.  
  
 La validación completa confirma que todas las variables de entorno a las que se hace referencia se encuentran dentro de los entornos a los que se hace referencia y que se incluyeron en la validación. Los resultados de la validación completa enumeran las referencias de entorno que no son válidas y las variables de entorno a las que se hace referencia que podrían no encontrarse en ninguno de los entornos a los que se hace referencia y que se incluyeron en la validación.  
  
  
