---
title: Configuración (objetos del sistema de carga) del proyecto (DB2ToSQL) | Documentos de Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-db2
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 9a545233-1b0a-488a-a1ec-c33aa608dcc1
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d6fa389cfe6dea25a8974a47a4c77024720da312
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="project-settingsloading-system-objects-db2tosql"></a>Configuración (objetos del sistema de carga) del proyecto (DB2ToSQL)
La página cargar objetos de sistema de la **configuración del proyecto** cuadro de diálogo permite especificar qué objetos del sistema DB2 SSMA se convierte y se carga en [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
El panel de objetos del sistema de carga está disponible en la **configuración del proyecto** y **configuración de proyecto predeterminada** cuadros de diálogo:  
  
-   Para especificar la configuración para todos los proyectos SSMA, en la **herramientas** menú, seleccione **la configuración predeterminada del proyecto**, seleccione el tipo de proyecto de migración para el que se requiere para puede ver o cambiar de configuración **versión de destino de migración** desplegable haga clic en **General** en la parte inferior del panel izquierdo y, a continuación, haga clic en **cargar objetos del sistema**.  
  
-   Para especificar la configuración para el proyecto actual, en la **herramientas** menú, seleccione **configuración del proyecto**, haga clic en **General** en la parte inferior del panel izquierdo y, a continuación, haga clic en **cargar objetos del sistema**.  
  
## <a name="default-settings"></a>Configuración predeterminada  
Convertir los objetos del sistema consume recursos del sistema y lleva tiempo. Para mejorar el rendimiento, SSMA selecciona sólo los objetos del sistema usados con más frecuencia, como se muestra en la lista siguiente:  
  
-   SYS. DBMS_OUTPUT  
  
-   SYS. DBMS_PIPE  
  
-   SYS. DBMS_UTILITY  
  
-   SYS. ESTÁNDAR  
  
-   SYS. UTL_FILE  
  
-   SYS.DBMS_LOB  
  
-   SYS.DBMS_SQL  
  
-   SYS. DBMS_SESSION  
  
Si los objetos de DB2 hacen referencia a objetos del sistema adicionales, debe seleccionar los objetos. Si no selecciona los objetos del sistema que hacen referencia los objetos de base de datos de DB2, SSMA va a notificar errores de conversión. Si recibe errores de conversión causados por falta de objetos del sistema, seleccione los objetos que faltan en este cuadro de diálogo. A continuación, puede repetir la conversión según sea necesario.  
  
