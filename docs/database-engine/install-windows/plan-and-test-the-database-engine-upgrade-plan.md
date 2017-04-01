---
title: "Planeaci&#243;n y prueba del plan de actualizaci&#243;n del motor de base de datos | Microsoft Docs"
ms.custom: ""
ms.date: "01/20/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "server-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19c5b725-7400-4881-af8f-fd232ca28234
caps.latest.revision: 16
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 16
---
# Planeaci&#243;n y prueba del plan de actualizaci&#243;n del motor de base de datos
  Para realizar una actualización a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] correcta, se precisa una planeación adecuada, con independencia del enfoque.  
  
## Notas de la versión y problemas conocidos de la actualización  
 Antes de actualizar el [!INCLUDE[ssDE](../../includes/ssde-md.md)], revise las [Notas de la versión de SQL Server 2016](../../sql-server/sql-server-2016-release-notes.md) y el tema [Compatibilidad con versiones anteriores del Motor de base de datos de SQL Server](../../database-engine/sql-server-database-engine-backward-compatibility.md).  
  
## Lista de comprobación de la planeación previa a la actualización  
 Antes de actualizar el [!INCLUDE[ssDE](../../includes/ssde-md.md)], consulte la siguiente lista de comprobación y los temas relacionados. Estos temas se aplican a todas las actualizaciones, al margen del método de actualización, y lo ayudarán a determinar cuál es el más adecuado: local, gradual o mediante una nueva instalación. Por ejemplo, es posible que no pueda realizar una actualización local o gradual si va a actualizar el sistema operativo, o bien si actualiza desde SQL Server 2005 o desde una versión de 32 bits de SQL Server. Para ver un árbol de decisión, consulte [Choose a Database Engine Upgrade Method](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md).  
  
-   **Requisitos de hardware y software:** revise los requisitos de hardware y software para instalar [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Podrá encontrarlos en [Hardware and Software Requirements for Installing SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md). Una parte de cualquier plan de ciclo de actualización es plantearse la actualización del hardware (el hardware más reciente es más rápido y puede reducir el número de licencias debido a menos procesadores o a la consolidación de los servidores y las bases de datos) y del sistema operativo. Estos tipos de cambios de hardware y software repercutirán en el tipo de método de actualización que elija.  
  
-   **Entorno actual:** investigue su entorno actual para descubrir los componentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que se utilizan y los clientes que se conectan a él.  
  
    -   **Proveedores de cliente:** aunque la actualización no requiere actualizar el proveedor para cada uno de los clientes, puede optar por hacerlo. Las siguientes características de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] bien requieren un proveedor actualizado para cada cliente, bien la actualización del proveedor ofrecerá una funcionalidad adicional:  
  
        -   [Always Encrypted &#40;motor de base de datos&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)  
  
        -   [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
        -   [Agentes de escucha de grupo de disponibilidad, conectividad de cliente y conmutación por error de una aplicación &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/listeners, client connectivity, application failover.md)  
  
        -   Actualización de seguridad SSL  
  
    -   **Componentes de terceros:** determine la compatibilidad de los componentes de terceros, como la copia de seguridad integrada.  
  
-   **Entorno de destino:** compruebe que el entorno de destino cumple los requisitos de hardware y software y puede admitir los requisitos del sistema original. Por ejemplo, la actualización puede conllevar la consolidación de varias instancias de SQL Server en una única instancia de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] nueva o la virtualización de su entorno de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en una nube privada o pública.  
  
-   **Edición:** determine la edición adecuada de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] para su actualización e identifique las rutas de actualización válidas para esta. Para obtener información detallada, vea [Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md). Antes de actualizar de una edición de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a otra, compruebe que las funciones que actualmente utiliza son compatibles con la edición a la que desea actualizar.  
  
    > [!NOTE]  
    >  Al actualizar a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] desde una versión anterior de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Edition, elija entre “Enterprise Edition: Licencia Core” y “Enterprise Edition”. Estas ediciones Enterprise solo se diferencian en los modos de licencia. Para obtener más información, consulte [Compute Capacity Limits by Edition of SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).  
  
-   **Compatibilidad con versiones anteriores:** consulte el tema sobre la compatibilidad con versiones anteriores del motor de base de datos de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] para ver los cambios en el comportamiento entre [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] y la versión de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] desde la que vaya a actualizar. Consulte [SQL Server Database Engine Backward Compatibility](../../database-engine/sql-server-database-engine-backward-compatibility.md).  
  
-   **Asesor de actualizaciones:**  ejecute el Asesor de actualizaciones de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] para ayudarlo a diagnosticar problemas que podrían bloquear el proceso de actualización o precisar la modificación de scripts o aplicaciones existentes debido a un cambio importante. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] contiene una nueva versión del Asesor de actualizaciones para ayudar a los clientes en la preparación de la actualización de un sistema existente.  Con esta herramienta, también podrá comprobar sus bases de datos existentes para ver si pueden aprovechar las nuevas características, como las tablas de Stretch, tras haber completado la actualización.   
    Puede descargar el Asesor de actualizaciones de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [aquí](https://www.microsoft.com/en-us/download/details.aspx?id=48119).  
  
-   **Comprobador de configuración del sistema: ** ejecute el Comprobador de configuración del sistema (SCC) de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] para determinar si el programa de instalación de SQL Server detecta cualquier problema de bloqueo antes de programar realmente la actualización. Para obtener más información, vea [Check Parameters for the System Configuration Checker](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md).  
  
-   **Actualizar las tablas con optimización para memoria:** al actualizar una instancia de base de datos de SQL Server 2014 que contenga tablas con optimización para memoria a SQL Server 2016, el proceso requiere un tiempo adicional para convertir dichas tablas en el nuevo formato en disco (y la base de datos estará sin conexión mientras se producen estos pasos).   La cantidad de tiempo depende del tamaño de las tablas con optimización para memoria y de la velocidad del subsistema de E/S. Se requieren tres operaciones de tamaño de datos en el caso de las actualizaciones locales y de nueva instalación (el paso 1 no es obligatorio en el caso de las actualizaciones graduales, pero los pasos 2 y 3, sí):  
  
    1.  Ejecute la recuperación de bases de datos con el formato en disco antiguo (esto incluye la carga de todos los datos de tablas con optimización para memoria en la memoria desde el disco).  
  
    2.  Serialice los datos en el disco en el nuevo formato en disco.  
  
    3.  Ejecute la recuperación de bases de datos con el nuevo formato (esto incluye la carga de todos los datos de tablas con optimización para memoria en la memoria desde el disco).  
  
     Además, si no hay suficiente espacio en disco durante este proceso, se producirá un error de recuperación. Asegúrese de que hay suficiente espacio en disco para almacenar la base de datos existente, más almacenamiento adicional, igual al tamaño actual de los contenedores del grupo de archivos MEMORY_OPTIMIZED_DATA de la base de datos, para realizar una actualización local o cuando se asocie una base de datos de SQL Server 2014 a una instancia de SQL Server 2016. Utilice la siguiente consulta para determinar el espacio en disco necesario para el grupo de archivos MEMORY_OPTIMIZED_DATA y, por lo tanto, también la cantidad de espacio libre en disco necesaria para que la actualización se realice correctamente:  
  
    ```  
    select cast(sum(size) as float)*8/1024/1024 'size in GB'   
    from sys.database_files  
    where data_space_id in (select data_space_id from sys.filegroups where type=N'FX')  
    ```  
  
## Desarrollo y prueba del plan de actualización  
 El mejor método consiste en tratar la actualización como cualquier otro proyecto de TI. Se recomienda organizar un equipo de actualización con conocimientos sobre la administración de bases de datos; redes; extracción, transformación y carga (ETL); y otras destrezas necesarias para llevar a cabo la actualización. El equipo debe realizar lo siguiente:  
  
-   **Elegir el método de actualización:** vea [Elección de un método de actualización del motor de base de datos](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md).  
  
-   **Desarrollar un plan de reversión:** la ejecución de este plan le permitirá restaurar el entorno original si se precisa la reversión.  
  
-   **Determinar los criterios de aceptación:** tendrá que saber que la actualización se ha producido correctamente antes de migrar a los usuarios al entorno actualizado.  
  
-   **Probar el plan de actualización:** para probar el rendimiento mediante la carga de trabajo real, use la utilidad Microsoft SQL Server Distributed Replay. Esta herramienta puede usar varios equipos para reproducir los datos de seguimiento, con lo que se simula una carga de trabajo crítica. Si realiza una reproducción en un servidor de prueba antes y después de una actualización de SQL Server, podrá medir las diferencias de rendimiento y buscar cualquier incompatibilidad que su aplicación pueda tener con la actualización. Para obtener más información, vea [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md) y [Opciones de línea de comandos de la herramienta de administración &#40;utilidad Distributed Replay&#41;](../../tools/distributed-replay/administration-tool-command-line-options-distributed-replay-utility.md).  
  
## ¿Le ayudó este artículo? Le escuchamos  
 ¿Qué información está buscando? ¿La encontró? Escuchamos sus comentarios para mejorar el contenido. Envíe sus comentarios a [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Plan%20and%20Test%20the%20Database%20Engine%20Upgrade%20Plan%20page).  
  
## Vea también  
 [Actualizar el motor de base de datos](../../database-engine/install-windows/upgrade-database-engine.md)  
  
  