---
title: Conectarse a la base de datos de SQL Azure (SybaseToSQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 96538007-1099-40c8-9902-edd07c5620ee
caps.latest.revision: 5
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c1656e76e6452c4394aad5eadb5d5b4073de9aac
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2018
---
# <a name="connect-to-azure-sql-db--sybasetosql"></a>Conectarse a la base de datos de SQL Azure (SybaseToSQL)
Use el cuadro de diálogo de la base de datos de SQL Azure para conectarse a la base de datos de la base de datos de SQL Azure que se va a migrar.  
  
Para tener acceso a este cuadro de diálogo, en la **archivo** menú, seleccione **conectar con base de datos de SQL Azure**. Si se ha conectado anteriormente, el comando es **conectarse de nuevo a la base de datos de SQL Azure.**  
  
## <a name="options"></a>Opciones  
**Nombre de servidor**  
  
Seleccione o escriba el nombre del servidor para conectarse a la base de datos de SQL Azure.  
  
**Base de datos**  
  
Seleccione, escriba o **examinar** el nombre de la base de datos.  
  
> [!IMPORTANT]  
> SSMA para Sybase no admite conexiones a la base de datos maestra en la base de datos de SQL Azure.  
  
**Nombre de usuario.**  
  
Escriba el nombre de usuario que va a usar para conectarse a la base de datos de la base de datos de SQL Azure SSMA  
  
**Contraseña**  
  
Escriba la contraseña del nombre de usuario.  
  
**Encrypt**  
  
SSMA recomienda conexión cifrada a la base de datos de SQL Azure.  
  
## <a name="create-azure-database"></a>Crear base de datos de Azure  
Si no hay ninguna base de datos de la cuenta de base de datos de SQL Azure, puede crear la primera base de datos.  
  
Para crear una nueva base de datos por primera vez, siga los pasos siguientes  
  
1.  Haga clic en el botón Examinar que se encuentra en la conexión al cuadro de diálogo de la base de datos de SQL Azure  
  
2.  Si no hay ninguna base de datos, aparecen los siguientes dos elementos de menú.  
  
    1.  **(no hay bases de datos que se encuentra)**  que está deshabilitada y atenuada todo el tiempo  
  
    2.  **Crear nueva base de datos** que está habilitada sólo cuando no hay ninguna base de datos en la cuenta de base de datos de SQL Azure. Al hacer clic en este elemento de menú, el cuadro de diálogo Crear base de datos de Azure está presente con el nombre de la base de datos y tamaño.  
  
3.  En el momento de creación de la base de datos, los dos parámetros siguientes se proporcionan como entrada:  
  
    1.  **Nombre de base de datos:** escriba el nombre de la base de datos.  
  
    2.  **Tamaño de base de datos:** seleccione el tamaño de base de datos que se debe crear en la cuenta de base de datos de SQL Azure.  
  
