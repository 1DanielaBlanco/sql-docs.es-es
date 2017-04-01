---
title: "Seguridad de DQS | Microsoft Docs"
ms.custom: ""
ms.date: "10/01/2012"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 921927f5-1b1e-452a-a79e-c691829fd826
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# Seguridad de DQS
  La infraestructura de seguridad de [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) está basada en la infraestructura de seguridad de SQL Server. Un administrador de bases de datos concede al usuario un conjunto de permisos mediante la asociación de dicho usuario a un rol de DQS. De este modo, determina los recursos de DQS a los que el usuario tiene acceso y las actividades funcionales que este puede realizar.  
  
## Roles de DQS  
 Existen cuatro roles para DQS. Uno es el administrador de bases de datos (DBA), que se ocupa principalmente de la instalación del producto, el mantenimiento de las bases de datos y la administración de los usuarios. Este rol se usa principalmente en SQL Server Management Studio en lugar de en la aplicación [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Su rol de servidor es sysadmin.  
  
 Los otros tres roles son trabajadores de la información, administradores de datos que utilizan el producto trabajando directamente en la aplicación [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Estos roles son los siguientes:  
  
-   La **Administrador de DQS** (rol dqs_administrator) puede hacer lo mismo en el ámbito del producto. El administrador puede modificar y ejecutar un proyecto, crear y modificar una base de conocimiento, terminar una actividad, detener un proceso dentro de una actividad y cambiar la configuración de Reference Data Services. El Administrador de DQS no puede, no obstante, instalar el servidor ni agregar nuevos usuarios. Es el administrador de bases de datos quien debe hacerlo.  
  
-   El **Editor de KB de DQS** (rol dqs_kb_editor) puede realizar todas las actividades DQS, excepto para la administración. El Editor de KB puede modificar y ejecutar un proyecto, y crear y modificar una base de conocimiento. Puede ver los datos de supervisión de las actividades, pero no puede terminar ni detener una actividad ni realizar labores administrativas.  
  
-   El **operador de KB de DQS** (rol dqs_kb_operator) puede modificar y ejecutar un proyecto. No puede realizar ningún tipo de tarea relacionada con la administración del conocimiento, ni puede crear ni cambiar una base de conocimiento. Puede ver los datos de supervisión de las actividades, pero no puede terminar una actividad ni realizar labores administrativas.  
  
## Administración de usuarios  
 El administrador de bases de datos (DBA) crea usuarios de DQS y los asocia a roles de DQS en SQL Server Management Studio. Para administrar los permisos, el DBA agrega inicios de sesión de SQL como usuarios de la base de datos DQS_MAIN y asocia cada usuario a uno de los roles de DQS. A cada rol se le conceden permisos de acceso a un conjunto de procedimientos almacenados de la base de datos DQS_MAIN. Los tres roles de DQS no están disponibles para las bases de datos DQS_PROJECTS y DQS_STAGING_DATA.  
  
## Tareas relacionadas  
  
|Descripción de la tarea|Tema|  
|----------------------|-----------|  
|Describe cómo crear un usuario y cómo concederle roles de DQS mediante SQL Server Management Studio.|[Administrar usuarios de DQS en SSMS](../Topic/Manage%20DQS%20Users%20in%20SSMS.md)|  
  
  