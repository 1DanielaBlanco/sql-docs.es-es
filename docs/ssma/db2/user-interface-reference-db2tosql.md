---
title: Referencia de la interfaz de usuario (DB2ToSQL) | Documentos de Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-db2
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 98ecc4ff-9416-48a2-af0f-86852cf69dab
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 6f361c8da435916e2a7293fe57a410a3b4d4c2a4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="user-interface-reference-db2tosql"></a>Referencia de la interfaz de usuario (DB2ToSQL)
Esta sección incluye temas de Ayuda [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) para DB2.  
  
## <a name="in-this-section"></a>En esta sección  
La tabla siguiente enumera los cuadros de diálogo SSMA:  
  
|||  
|-|-|  
|Tema|Description|  
|[Objeto selección avanzada de &#40;DB2ToSQL&#41;](../../ssma/db2/advanced-object-selection-db2tosql.md)|Use la **avanzadas seleccione objeto** cuadro de diálogo para buscar objetos de base de datos mediante el uso de criterios de filtro y, a continuación, active o desactive los objetos.|  
|[Informe de evaluación &#40;DB2ToSQL&#41;](../../ssma/db2/assessment-report-db2tosql.md)|Utilice el informe de evaluación para ver los resultados de la conversión de objetos de DB2 a [!INCLUDE[tsql](../../includes/tsql_md.md)] sintaxis y para calcular el tiempo y la complejidad de una migración a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|[Conectarse a la base de datos DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/connecting-to-db2-database-db2tosql.md)|Use la **conectar a DB2** cuadro de diálogo para conectarse a la base de datos de DB2 que se va a migrar.|  
|[Conectarse a SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/connect-to-sql-server-db2tosql.md)|Use la **conectar con SQL Server** cuadro de diálogo para conectarse a la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] para que van a migrar.|  
|[Informe de migración de datos &#40;DB2ToSQL&#41;](../../ssma/db2/data-migration-report-db2tosql.md)|Muestra los resultados de migración de datos de DB2 a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|[Configuración de la migración de datos](http://msdn.microsoft.com/en-us/573e673e-a194-4cb2-9aba-aaac6e1a225c)|Use la **configuración de migración de datos extendida** tab para escribir consultas personalizadas para la migración de datos.|  
|[Editar la asignación de tipo &#40;DB2ToSQL&#41;](../../ssma/db2/edit-type-mapping-db2tosql.md)|Use la **nueva asignación de tipo** o **Editar asignación de tipo** cuadros de diálogo para crear o modificar la asignación de tipos de datos entre los objetos de base de datos y las bases de datos de origen y de destino.|  
|[Configuración global &#40;Editor&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/global-settings-editor-db2tosql.md)|Utilice la página del Editor de la **configuración Global** cuadro de diálogo para configurar las opciones del editor de código.|  
|[Configuración global &#40;cuadros de diálogo&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/global-settings-dialogs-db2tosql.md)|Use la página de los cuadros de diálogo de la **configuración Global** cuadro de diálogo para configurar opciones de advertencia y de cuadro de diálogo predeterminado.|  
|[Configuración global &#40;registro&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/global-settings-logging-db2tosql.md)|Use la página de registro de la **configuración Global** cuadro de diálogo para configurar el registro.|  
|[Configuración global &#40;ventana de salida&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/global-settings-output-window-db2tosql.md)|Use la **configuración Global** cuadro de diálogo para establecer preferencias sobre el SSMA para la interfaz de usuario de DB2.|  
|[Nuevo proyecto &#40;DB2ToSQL&#41;](../../ssma/db2/new-project-db2tosql.md)|Use la **nuevo proyecto** cuadro de diálogo para crear un nuevo SSMA para proyecto de DB2.|  
|[Configuración del proyecto &#40;conversión&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md)|Use la página de conversión de la **configuración del proyecto** cuadro de diálogo para especificar cómo SSMA para DB2 convierte las funciones y variables globales.|  
|[Configuración del proyecto &#40;GUI&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-gui-db2tosql.md)|Use la página de la interfaz gráfica de usuario de la **configuración del proyecto** cuadro de diálogo para especificar la cantidad de datos que aparece en el **datos** ficha.|  
|[Configuración del proyecto &#40;migración&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-migration-db2tosql.md)|Utilice la página de migración de la **configuración del proyecto** cuadro de diálogo para personalizar cómo SSMA para DB2 migra datos de DB2 a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|[Configuración del proyecto&#40;sincronización&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-synchronization-db2tosql.md)|Use la página de sincronización de la **configuración del proyecto** cuadro de diálogo para personalizar cómo SSMA para DB2 crea o modifica migra objetos de base de datos en [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|[Configuración del proyecto&#40;objetos del sistema de carga&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-loading-system-objects-db2tosql.md)|Utilice la página cargar objetos de sistema de la **configuración del proyecto** convierte y se carga en el cuadro de diálogo para especificar qué sistema DB2 objetos SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].|  
|[Configuración del proyecto &#40;la asignación de tipo&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-type-mapping-db2tosql.md)|Use la página de asignación de tipo de la **configuración del proyecto** cuadro de diálogo para especificar las asignaciones de tipos de valor predeterminado para todas las bases de datos y objetos de base de datos de SSMA para proyecto de DB2.|  
|[Actualizar desde la base de datos &#40;DB2ToSQL&#41;](../../ssma/db2/refresh-from-database-db2tosql.md)|Use la **actualizar desde la base de datos** cuadro de diálogo para seleccionar objetos para actualizar desde la base de datos DB2.|  
|[Guardar metadatos &#40;DB2ToSQL&#41;](../../ssma/db2/save-metadata-db2tosql.md)|El **guardar metadatos** cuadro de diálogo aparece cuando se guarda un proyecto que le faltan metadatos.|  
  
## <a name="see-also"></a>Vea también  
[Introducción a SSMA para DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/getting-started-with-ssma-for-db2-db2tosql.md)  
[Bases de datos de DB2 migrar a SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
