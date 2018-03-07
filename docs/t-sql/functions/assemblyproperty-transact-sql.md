---
title: ASSEMBLYPROPERTY (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ASSEMBLYPROPERTY_TSQL
- ASSEMBLYPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- ASSEMBLYPROPERTY statement
- assemblies [CLR integration], properties
ms.assetid: cf03d1b1-724c-48bf-a8df-3fe2586b150a
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a38d9f773e010ab779204d7c92b351d88c0d08f7
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="assemblyproperty-transact-sql"></a>ASSEMBLYPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Devuelve información sobre una propiedad de un ensamblado.
  
![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintaxis  
  
```sql
ASSEMBLYPROPERTY('assembly_name', 'property_name')  
```  
  
## <a name="arguments"></a>Argumentos  
*assembly_name*  
Es el nombre del ensamblado.
  
*property_name*  
Es el nombre de una propiedad de la que se va a recuperar información. *property_name* puede ser uno de los siguientes valores.
  
|Value|Description|  
|---|---|
|**CultureInfo**|Configuración regional del ensamblado.|  
|**PublicKey**|Clave pública o símbolo (token) de clave pública del ensamblado.|  
|**MvID**|Número completo de identificación de versión del ensamblado generado por el compilador.|  
|**VersionMajor**|Componente principal (primera parte) del número de identificación de la versión de cuatro partes del ensamblado.|  
|**VersionMinor**|Componente secundario (segunda parte) del número de identificación de la versión de cuatro partes del ensamblado.|  
|**VersionBuild**|Componente de generación (tercera parte) del número de identificación de la versión de cuatro partes del ensamblado.|  
|**VersionRevision**|Componente de revisión (cuarta parte) del número de identificación de la versión de cuatro partes del ensamblado.|  
|**SimpleName**|Nombre sencillo del ensamblado.|  
|**Arquitectura**|Arquitectura del procesador del ensamblado.|  
|**CLRName**|Cadena canónica que codifica el nombre sencillo, número de versión, referencia cultural, clave pública y arquitectura del ensamblado. Este valor identifica de forma única el ensamblado en Common Language Runtime (CLR).|  
  
## <a name="return-type"></a>Tipo de valor devuelto
**sql_variant**
  
## <a name="examples"></a>Ejemplos  
En el ejemplo siguiente, se supone que se registra un ensamblado de `HelloWorld` en la base de datos [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Para obtener más información, consulte [ejemplo Hello World](http://msdn.microsoft.com/library/fed6c358-f5ee-4d4c-9ad6-089778383ba7).
  
```sql
USE AdventureWorks2012;  
GO  
SELECT ASSEMBLYPROPERTY ('HelloWorld' , 'PublicKey');  
```  
  
## <a name="see-also"></a>Vea también
[CREATE ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/create-assembly-transact-sql.md)  
[DROP ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-assembly-transact-sql.md)
  
  
