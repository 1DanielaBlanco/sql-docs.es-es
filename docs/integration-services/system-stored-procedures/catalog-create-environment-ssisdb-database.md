---
title: catalog.create_environment (base de datos de SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 66367092-9f6e-40e6-90bd-81efb078ab70
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3b0ff9e5c2a5874b5ff01e8da19fa6015e28b5e2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47778563"
---
# <a name="catalogcreateenvironment-ssisdb-database"></a>catalog.create_environment (base de datos de SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Crea un entorno en el catálogo de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```sql  
catalog.create_environment [@folder_name =] folder_name  
     , [@environment_name =] environment_name  
  [  , [@environment_description =] environment_description ]  
```  
  
## <a name="arguments"></a>Argumentos  
 [@folder_name =] *folder_name*  
 Nombre de la carpeta que contendrá el entorno. *folder_name* es **nvarchar(128)**.  
  
 [@environment_name =] *environment_name*  
 El nombre del entorno. *environment_name* es **nvarchar(128)**.  
  
 [@environment_description=] *environment_description*  
 Una descripción opcional del entorno. *environment_description* es **nvarchar(1024)**.  
  
## <a name="return-code-value"></a>Valor de código de retorno  
 0 (correcto)  
  
## <a name="result-sets"></a>Conjuntos de resultados  
 None  
  
## <a name="permissions"></a>Permisos  
 Este procedimiento almacenado necesita uno de los permisos siguientes:  
  
-   Permisos READ y MODIFY en la carpeta  
  
-   Pertenencia al rol de base de datos de **ssis_admin**  
  
-   rol de base de datos  
  
-   Pertenencia al rol de servidor de **sysadmin**  
  
## <a name="errors-and-warnings"></a>Errores y advertencias  
 En la siguiente lista se describen algunas condiciones que pueden producir un error o una advertencia:  
  
-   El nombre de la carpeta no se encuentra  
  
-   Un entorno con el mismo nombre ya existe en la carpeta especificada  
  
## <a name="remarks"></a>Notas  
 El nombre del entorno debe ser único en la carpeta.  
  
  
