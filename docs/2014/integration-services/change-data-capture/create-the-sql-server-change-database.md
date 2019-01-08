---
title: Crear la base de datos de cambios de SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- oraIns
ms.assetid: 4f79c24a-e99a-4a06-8637-51eeec406259
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7e95a47f2a2fc7444822c19b67bf2d95626fa62c
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2018
ms.locfileid: "52770977"
---
# <a name="create-the-sql-server-change-database"></a>Crear la base de datos de cambios de SQL Server
  Cuando se inicia el Asistente para nueva instancia, se abre la página Crear base de datos CDC. Use la página Crear base de datos CDC para proporcionar información sobre la nueva instancia CDC y crear una nueva base de datos Cambios.  
  
 Cuando se crea una nueva base de datos CDC, se habilita para CDC de SQL Server y esta habilitación necesita un inicio de sesión que sea miembro del rol fijo de servidor `sysadmin` .  
  
 Cuando un usuario que inicia el Asistente para crear una instancia CDC de Oracle no es miembro del rol fijo de servidor `sysadmin` , se abre el cuadro de diálogo Conectar con SQL Server y solicita las credenciales para un miembro del rol sysadmin para realizar la tarea Habilitar la base de datos para CDC de SQL Server. Cuando se crea la base de datos CDC, el inicio de sesión `sysadmin` se descarta y se reanuda el trabajo con el inicio de sesión original de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usado cuando se entró en la Consola del diseñador de Oracle.  
  
> [!IMPORTANT]  
>  Para otras tareas distintas de Habilitar la base de datos para CDC de SQL Server, el inicio de sesión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usado para ejecutar el Asistente para nueva instancia debe tener el rol fijo de servidor `dbcreator` y permisos UPDATE en la base de datos MSXDBCDC.  
  
 Para obtener información acerca de cómo escribir los datos en el cuadro de diálogo Conectar con SQL Server, vea [SQL Server Connection for Instance Creation](sql-server-connection-for-instance-creation.md).  
  
## <a name="options"></a>Opciones  
 **Instancia CDC de Oracle**  
 Escriba la siguiente información sobre la instancia de CDC que está creando.  
  
-   **Nombre**: Escriba un nombre para el nuevo servicio. También será el nombre de la nueva base de datos Cambios.  
  
-   **Descripción**: Escriba una descripción para la nueva instancia que le ayude a identificarla. Esto es opcional.  
  
 **Base de datos de cambios de SQL Server**  
 Esta sección se emplea para crear la base de datos.  
  
1.  **Cambiar base de datos**: El nombre de la nueva base de datos de cambio. El nombre de la base de datos es el mismo que el que asignó a la instancia. Este campo de solo lectura muestra la ruta de acceso completa a la base de datos.  
  
2.  **Crear base de datos**: Haga clic en **Create Database** para crear la base de datos.  
  
     Para crear la base de datos, el inicio de sesión debe tener el rol de servidor `sysasmin` . Vea la nota de seguridad anterior para obtener más información.  
  
     Después de crear la base de datos, puede hacer clic en **Siguiente** para [Connect to an Oracle Source Database](connect-to-an-oracle-source-database.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo crear la instancia de base de datos de cambios de SQL Server](how-to-create-the-sql-server-change-database-instance.md)   
 [El servicio CDC de Oracle](the-oracle-cdc-service.md)  
  
  
