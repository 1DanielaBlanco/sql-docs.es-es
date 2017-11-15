---
title: "external scripts enabled (opción de configuración del servidor) | Microsoft Docs"
ms.custom: SQL2016_New_Updated
ms.date: 08/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- external scripts enabled
- external_scripts_enabled_TSQL
helpviewer_keywords: external scripts enabled option
ms.assetid: 9d0ce165-8719-4007-9ae8-00f85cab3a0d
caps.latest.revision: "9"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 05c5af488241c28a5b83c01ac089fa5e1e1715c0
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="external-scripts-enabled-server-configuration-option"></a>Opción de configuración de servidor Scripts externos habilitados
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Utilice la opción **external scripts enabled** para habilitar la ejecución de scripts con determinadas extensiones de lenguaje remoto. Esta propiedad está DESACTIVADA de forma predeterminada. El programa de instalación, opcionalmente, puede establecer esta propiedad en true si **Advanced Analytics Services** (Servicios de análisis avanzado) está instalado.  
  

 Debe habilitar la opción de script externo habilitado antes de poder ejecutar un script externo mediante el procedimiento **sp_execute_external_script** . Use **sp_execute_external_script** para ejecutar scripts escritos en un lenguaje compatible, como R. En [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] consta de un componente de servidor instalado con [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], y un conjunto de herramientas de estación de trabajo y bibliotecas de conectividad que conectan a los científicos de datos al entorno de alto rendimiento de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Instale la característica **Extensiones de análisis avanzado** durante la instalación de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para habilitar la ejecución de los scripts de R. Para obtener más información, consulte [Installing Previous Versions of SQL Server R Services](http://msdn.microsoft.com/library/48380645-9e72-4744-bebb-1c1fd8a18c43).  
  
 Ejecute el script siguiente para habilitar los scripts externos:  
  
```  
sp_configure 'external scripts enabled', 1;  
RECONFIGURE WITH OVERRIDE;  
```  
  
 Debe reiniciar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para que este cambio surta efecto.  
  
## <a name="see-also"></a>Vea también  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)   
 [SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services.md)  
  
  
