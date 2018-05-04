---
title: Asignación de esquemas de Sybase ASE a esquemas SQL Server (SybaseToSQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Schema Mapping
ms.assetid: 2c927003-c49d-4fe1-8e3e-5b2899166268
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: c712831f4db10fd10f0d635fc43779c39b0f8953
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql"></a>Asignación de Sybase ASE esquemas a esquemas SQL Server (SybaseToSQL)
En Sybase Adaptive Server Enterprise (ASE), cada base de datos tiene uno o más esquemas. De forma predeterminada, SSMA migra todos los objetos de una base de datos y el esquema a la misma base de datos y esquema de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. Sin embargo, puede personalizar la asignación entre ASE y [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o bases de datos de SQL Azure y esquemas.  
  
## <a name="ase-and-sql-server-or-sql-azure-schemas"></a>ASE y SQL Server o SQL Azure esquemas  
ASE y [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure especificar bases de datos y sus esquemas mediante la notación de dos parte como *database.schema*. Por ejemplo, en un ASE **demostración** la base de datos, podría haber un **dbo** esquema. Que el par de base de datos y el esquema se especifica como **demo.dbo**. Si [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure tiene la misma base de datos y el esquema, el par también se especifica como **demo.dbo**.  
  
## <a name="modifying-the-target-database-and-schema"></a>Modificación de la base de datos de destino y el esquema  
En SSMA, puede asignar un esquema ASE a disponibles [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o esquema de SQL Azure.  
  
**Para modificar la base de datos y esquema**  
  
1.  En el Explorador de metadatos de Sybase, seleccione **bases de datos**.  
  
    El **esquema de asignación** ficha también está disponible cuando se selecciona una base de datos individual, el **esquemas** carpeta o esquemas individuales. La lista en la **esquema de asignación** ficha se personaliza para el objeto seleccionado.  
  
2.  En el panel derecho, haga clic en el **esquema de asignación** ficha.  
  
    Verá una lista de todas las bases de datos de ASE con sus esquemas, seguidos por un valor de destino. Este destino se indica en la notación de dos partes (*database.schema*) en [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o que se migrarán los objetos y datos de SQL Azure.  
  
3.  Seleccione la fila que contiene la asignación que desea cambiar y, a continuación, haga clic en **modificar**.  
  
4.  En el **elegir el esquema de destino** cuadro de diálogo, puede buscar base de datos de destino disponibles y el esquema o el tipo de la base de datos y el esquema de nombre en el cuadro de texto en una notación de dos partes (database.schema) y, a continuación, haga clic en **Aceptar**.  
  
5.  El destino se cambia en el **esquema de asignación** ficha.  
  
**Modos de asignación**  
  
-   Asignar a SQL Server  
  
Base de datos de origen se puede asignar a cualquier base de datos de destino. De forma predeterminada se asigna la base de datos de origen a destino [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de datos con el que se ha conectado con SSMA. Si la base de datos de destino que va a asignar es no existente en [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], a continuación, se le pedirá con un mensaje **"la base de datos o el esquema no existe en el destino [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] metadatos. Se crearán durante la sincronización. ¿Desea continuar?"** Haga clic en Sí. De igual forma, se puede asignar el esquema al esquema no existe en el destino [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] base de datos que se creará durante la sincronización.  
  
-   Asignación a SQL Azure  
  
Puede asignar la base de datos de origen a la base de datos de SQL Azure de destino conectados o a cualquier esquema de la base de datos de SQL Azure de destino conectados. Si asignar el esquema de origen ningún esquema no existe en la base de datos de destino conectados, se le pedirá con un mensaje **"esquema no existe en los metadatos de destino. Se crearán durante la sincronización. ¿Desea continuar? "** Haga clic en Sí.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Revertir a la base de datos predeterminada y el esquema  
Si personaliza la asignación entre un esquema ASE y un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o esquema de SQL Azure, puede revertir la asignación a los valores predeterminados.  
  
**Para revertir a la base de datos predeterminada y el esquema**  
  
1.  En la pestaña asignación de esquema, seleccione una fila y haga clic en **Restablecer valores predeterminados** para revertir a la base de datos predeterminada y el esquema.  
  
## <a name="next-steps"></a>Pasos siguientes  
Si desea analizar la conversión de objetos de Sybase ASE en [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] u objetos de SQL Azure, también puede [crear un informe de conversión](http://msdn.microsoft.com/en-us/eb996b7c-1eef-4f73-b5e6-2fa6faf7336c). En caso contrario, puede [convertir las definiciones de objeto de base de datos de ASE](http://msdn.microsoft.com/en-us/509cb65d-2f54-427a-83d7-37919cc4e3e3) en [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o definiciones de objetos de SQL Azure.  
  
## <a name="see-also"></a>Vea también  
[Migrar bases de datos de Sybase ASE a SQL Server: base de datos de SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
