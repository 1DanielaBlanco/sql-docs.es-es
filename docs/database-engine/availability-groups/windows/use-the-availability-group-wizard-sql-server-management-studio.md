---
title: "Usar el Asistente para grupo de disponibilidad (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.newagwizard.f1"
  - "sql13.swb.newavgroupwiz.f1"
helpviewer_keywords: 
  - "Asistente para nuevo grupo de disponibilidad, réplicas de disponibilidad"
  - "Grupos de disponibilidad [SQL Server], asistentes"
  - "grupos de disponibilidad [SQL Server], crear"
ms.assetid: e1f1dccc-9e65-471d-8fd1-b45085c9484a
caps.latest.revision: 46
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 45
---
# Usar el Asistente para grupo de disponibilidad (SQL Server Management Studio)
  En este tema se describe cómo se usa el Asistente para nuevo grupo de disponibilidad (en [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]) para crear y configurar un grupo de disponibilidad AlwaysOn en [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Un *grupo de disponibilidad* define un conjunto de bases de datos de usuario que realizarán la conmutación por error como una sola unidad y un conjunto de asociados de conmutación por error, conocido como *réplicas de disponibilidad*, que admiten la conmutación por error.  
  
> [!NOTE]  
>  Para obtener una introducción a los grupos de disponibilidad, vea [Información general de los grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).  
  
-   **Antes de empezar:**  
  
     [Requisitos previos, restricciones y recomendaciones](#Prerequisites)  
  
     [Seguridad](#Security)  
  
-   **Para crear y configurar un grupo disponibilidad con: ** [Asistente para nuevo grupo de disponibilidad (SQL Server Management Studio)](#RunAGwiz)  
  
> [!NOTE]  
>  Como alternativa al uso del Asistente para nuevo grupo de disponibilidad, puede utilizar cmdlets de [!INCLUDE[tsql](../../../includes/tsql-md.md)] o [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Para obtener más información, vea [Crear un grupo de disponibilidad &#40;Transact-SQL&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md) o [Crear un grupo de disponibilidad &#40;SQL Server PowerShell&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-sql-server-powershell.md).  
  
##  <a name="BeforeYouBegin"></a> Antes de empezar  
 Se recomienda encarecidamente leer esta sección antes de intentar crear el primer grupo de disponibilidad.  
  
###  <a name="Prerequisites"></a> Requisitos previos, restricciones y recomendaciones  
 En la mayoría de los casos, puede usar el Asistente para nuevo grupo de disponibilidad para realizar todas las tareas necesarias para crear y configurar un grupo de disponibilidad. Sin embargo, puede que tenga que completar algunas tareas manualmente:  
  
-   Antes de crear un grupo de disponibilidad, compruebe que las instancias de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que hospedan réplicas de disponibilidad residen en otro nodo (WSFC) de clúster de conmutación por error de Windows Server en el mismo clúster de conmutación por error de WSFC. Además, compruebe que cada una de las instancias del servidor cumple los requisitos previos de [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Para obtener más información, recomendamos encarecidamente que lea [Requisitos previos, restricciones y recomendaciones para Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs, restrictions, recommendations - always on availability.md).  
  
-   Si una instancia de servidor seleccionada para hospedar una réplica de disponibilidad se ejecuta bajo una cuenta de usuario de dominio y no tiene todavía un extremo de creación de reflejo de la base de datos, el asistente puede crear el extremo y conceder el permiso CONNECT a la cuenta de servicio de la instancia de servidor. Sin embargo, si el servicio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] se ejecuta como una cuenta integrada (como sistema local, servicio local o servicio de red), o una cuenta que no es de dominio, debe usar certificados para la autenticación de extremos y el asistente no podrá crear un extremo de creación de reflejo de la base de datos en la instancia de servidor. En este caso, se recomienda crear los extremos de creación de reflejo de la base de datos manualmente antes de iniciar el Asistente para nuevo grupo de disponibilidad.  
  
     **Para usar certificados para un punto de conexión de creación de reflejo de la base de datos:**  
  
     [CREATE ENDPOINT &#40;Transact-SQL&#41;](../../../t-sql/statements/create-endpoint-transact-sql.md)  
  
     [Usar certificados para un punto de conexión de creación de reflejo de la base de datos &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   Las instancias de clúster de conmutación por error (FCI) de SQL Server no admiten la conmutación automática por error de grupos de disponibilidad, por lo tanto, todas las réplicas de disponibilidad hospedadas por un FCI solo se pueden configurar para la conmutación por error manual.  
  
-   **Requisitos previos para que el asistente realice la sincronización de datos inicial completa**  
  
    -   Todas las rutas de acceso de archivos de base de datos deben ser idénticas en todas las instancias de servidor que hospedan una réplica para el grupo de disponibilidad.  
  
    -   Ningún nombre de base de datos principal puede existir en ninguna instancia de servidor que hospede una réplica secundaria. Esto significa que ninguna de las nuevas bases de datos secundarias puede existir todavía.  
  
    -   Tendrá que especificar un recurso compartido de red para que el asistente cree y obtenga acceso a las copias de seguridad. Para la réplica principal, la cuenta usada para iniciar el [!INCLUDE[ssDE](../../../includes/ssde-md.md)] debe tener permisos del sistema de archivos de lectura y escritura en un recurso compartido de red. Para las réplicas secundarias, la cuenta debe tener permiso de lectura en el recurso compartido de red.  
  
        > [!IMPORTANT]  
        >  Las copias de seguridad de registros serán parte de la cadena de copias de seguridad de registros. Almacene adecuadamente los archivos de copia de seguridad del registro.  
  
     Si no puede utilizar el asistente para realizar la sincronización de datos inicial completa, debe preparar las bases de datos secundarias manualmente. Puede hacerlo antes o después de ejecutar el asistente. Para obtener más información, vea [Preparar manualmente una base de datos secundaria para un grupo de disponibilidad &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
###  <a name="Security"></a> Seguridad  
  
####  <a name="Permissions"></a> Permisos  
 Se requiere la pertenencia al rol fijo de servidor **sysadmin** y el permiso de servidor CREATE AVAILABILITY GROUP, el permiso ALTER ANY AVAILABILITY GROUP o el permiso CONTROL SERVER.  
  
 También se necesita el permiso CONTROL ON ENDPOINT si desea permitir que el Asistente para nuevo grupo de disponibilidad administre el extremo de creación de reflejo de la base de datos.  
  
##  <a name="RunAGwiz"></a> Utilizar el Asistente para nuevo grupo de disponibilidad  
  
1.  En el Explorador de objetos, conéctese a la instancia del servidor que hospeda la réplica principal.  
  
2.  Expanda los nodos **Alta disponibilidad de AlwaysOn** y **Grupos de disponibilidad**.  
  
3.  Para iniciar el Asistente para nuevo grupo de disponibilidad, seleccione el comando **Asistente para nuevo grupo de disponibilidad** .  
  
4.  La primera vez que se ejecuta este asistente, aparece una página **Introducción** . Para omitir esta página en el futuro, puede hacer clic en **No volver a mostrar esta página**. Después de leer esta página, haga clic en **Siguiente**.  
  
5.  En la página **Especificar nombre de grupo de disponibilidad** , escriba el nombre del nuevo grupo de disponibilidad en el campo **Nombre de grupo de disponibilidad** . Este nombre debe ser un identificador válido de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que sea único en el clúster de conmutación por error de WSFC y el dominio en conjunto. La longitud máxima del nombre de un grupo de disponibilidad es 128 caracteres.  
  
6.  En la página **Seleccionar bases de datos** , la cuadrícula enumera las bases de datos de la instancia del servidor conectado que se pueden convertir en *bases de datos de disponibilidad*. Seleccione una o varias de las bases de datos enumeradas para participar como bases de datos de disponibilidad en el nuevo grupo de disponibilidad. Estas bases de datos serán inicialmente las *bases de datos principales*iniciales.  
  
     Para cada base de datos de la lista, la columna **Tamaño** muestra el tamaño de la base de datos, si se conoce. La columna **Estado** indica si una base de datos determinada cumple los [requisitos previos](../../../database-engine/availability-groups/windows/prereqs, restrictions, recommendations - always on availability.md) de las bases de datos de disponibilidad. Si los requisitos previos no se cumplen, una breve descripción de estado indica el motivo por el que la base de datos no es apta; por ejemplo, si no utiliza el modelo de recuperación completa. Para obtener más información, haga clic en la descripción del estado.  
  
     Si cambia una base de datos para que pueda ser apta, haga clic en **Actualizar** para actualizar la cuadrícula de bases de datos.  
  
     Si la base de datos contiene una clave maestra de base de datos, escriba la contraseña para dicha clave en la columna **Contraseña** .  
  
7.  En la página **Especificar réplicas** , especifique y configure una o varias réplicas para el nuevo grupo de disponibilidad. Esta página contiene cuatro pestañas: En la siguiente tabla se presentan estas pestañas. Para obtener más información, vea el tema [Especificar la página de réplicas &#40;Asistente para nuevo grupo de disponibilidad/Asistente para agregar réplica&#41;](../../../database-engine/availability-groups/windows/specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md).  
  
    |Pestaña|Descripción breve|  
    |---------|-----------------------|  
    |**Réplicas**|Utilice esta pestaña para especificar cada instancia de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que hospedará una réplica secundaria. Tenga en cuenta que la instancia de servidor a la que está conectado actualmente debe hospedar la réplica principal.|  
    |**Extremos**|Utilice esta pestaña para comprobar los extremos de creación de reflejo de base de datos existentes y también, si este extremo falta en una instancia de servidor cuyas cuentas de servicio utilizan la autenticación de Windows, para crear el extremo automáticamente.<br /><br /> Nota: Si cualquier instancia de servidor se ejecuta bajo una cuenta de usuario que no es de dominio, se debe realizar un cambio manual en la instancia de servidor antes de continuar con el asistente. Para obtener más información, vea [Requisitos previos](#Prerequisites), anteriormente en este tema.|  
    |**Preferencias de copia de seguridad**|Utilice esta pestaña para especificar sus preferencias de copias de seguridad para el grupo de disponibilidad en conjunto y las prioridades de copias de seguridad para las réplicas de disponibilidad individuales.|  
    |**Escucha**|Utilice esta pestaña para crear un agente de escucha del grupo de disponibilidad. De forma predeterminada, el asistente no crea un agente de escucha.|  
  
8.  En la página **Seleccionar sincronización de datos iniciales** , elija cómo desea que las nuevas bases de datos secundarias se creen y se unan al grupo de disponibilidad. Elija una de las opciones siguientes:  
  
    -   **Completa**  
  
         Seleccione esta opción si el entorno cumple los requisitos para iniciar automáticamente la sincronización de datos iniciales (para obtener más información, vea [Requisitos previos, restricciones y recomendaciones](#Prerequisites), anteriormente en este tema).  
  
         Si selecciona **Completa**, después de crear el grupo de disponibilidad, el asistente realizará una copia de seguridad de cada base de datos principal y su registro de transacciones a un recurso compartido de red y restaurará las copias de seguridad en cada instancia de servidor que hospeda una réplica secundaria. El asistente unirá entonces cada base de datos secundaria al grupo de disponibilidad.  
  
         En el campo **Especificar una ubicación de red compartida accesible por todas las réplicas:**, especifique un recurso compartido de copia de seguridad al que todas las instancias del servidor que hospedan réplicas tengan acceso de lectura/escritura. Para obtener más información, vea [Requisitos previos](#Prerequisites), anteriormente en este tema.  
  
    -   **Solo unión**  
  
         Si ha preparado manualmente las bases de datos secundarias de las instancias de servidor que hospedarán las réplicas secundarias, puede seleccionar esta opción. El asistente unirá las bases de datos secundarias existentes al grupo de disponibilidad.  
  
    -   **Omitir la sincronización de datos iniciales**  
  
         Seleccione esta opción si desea usar sus propias bases de datos y copias de seguridad de registros de sus bases de datos principales. Para obtener más información, vea [Iniciar el movimiento de datos en una base de datos secundaria AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/start-data-movement-on-an-always-on-secondary-database-sql-server.md).  
  
9. La página **Validación** comprueba si los valores especificados en este asistente cumplen los requisitos del Asistente para nuevo grupo de disponibilidad. Para realizar un cambio, haga clic en **Anterior** para volver a una página anterior del asistente con el fin de cambiar uno o varios valores. Haga clic en **Siguiente** para volver a la página **Validación** y haga clic en **Volver a ejecutar la validación**.  
  
10. En la página **Resumen** , revise las opciones para el nuevo grupo de disponibilidad. Para realizar un cambio, haga clic en **Anterior** para volver a la página correspondiente. Después de realizar el cambio, haga clic en **Siguiente** para volver a la página **Resumen** .  
  
    > [!IMPORTANT]  
    >  Cuando la cuenta de servicio de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de una instancia de servidor que va a hospedar una nueva réplica de disponibilidad no existe ya como inicio de sesión, el Asistente para nuevo grupo de disponibilidad debe crear el inicio de sesión. En la página **Resumen** , el asistente muestra la información del inicio de sesión que se va a crear. Si hace clic en **Finalizar**, el asistente creará este inicio de sesión para la cuenta de servicio de SQL Server y le concederá el permiso CONNECT.  
  
     Si está satisfecho con las selecciones, puede hacer clic en **Script** para crear un script de los pasos que ejecutará el asistente. A continuación, para crear y configurar el nuevo grupo de disponibilidad, haga clic en **Finalizar**.  
  
11. En la página **Progreso** se muestra el progreso de los pasos necesarios para crear el grupo de disponibilidad (configuración de puntos de conexión, creación del grupo de disponibilidad y unión de la réplica secundaria al grupo).  
  
12. Según se completen estos pasos, la página **Resultados** mostrará el resultado de cada paso. Si todos estos pasos se realizan correctamente, el nuevo grupo de disponibilidad se configura por completo. Si cualquiera de los pasos produce un error, quizás necesite completar manualmente la configuración o usar un asistente para el paso con error. Para obtener información sobre la causa de un error determinado, haga clic en el vínculo “Error” asociado de la columna **Resultado** .  
  
     Una vez completado el asistente, haga clic en **Cerrar** para salir.  
  
##  <a name="RelatedTasks"></a> Tareas relacionadas  
 **Para completar la configuración del grupo de disponibilidad**  
  
-   [Combinar una réplica secundaria con un grupo de disponibilidad &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Preparar manualmente una base de datos secundaria para un grupo de disponibilidad &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Combinar una base de datos secundaria con un grupo de disponibilidad &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Crear o configurar un agente de escucha de grupo de disponibilidad &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)  
  
 **Maneras alternativas de crear un grupo de disponibilidad**  
  
-   [Usar el cuadro de diálogo Nuevo grupo de disponibilidad &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Crear un grupo de disponibilidad &#40;Transact-SQL&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)  
  
-   [Crear un grupo de disponibilidad &#40;SQL Server PowerShell&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-sql-server-powershell.md)  
  
 **Para habilitar los grupos de disponibilidad AlwaysOn**  
  
-   [Habilitar y deshabilitar grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 **Para configurar un extremo de creación del reflejo de la base de datos**  
  
-   [Crear un punto de conexión de creación de reflejo de la base de datos para grupos de disponibilidad AlwaysOn &#40;SQL Server PowerShell&#41;](../../../database-engine/availability-groups/windows/database mirroring - always on availability groups- powershell.md)  
  
-   [Crear un punto de conexión de creación de reflejo de la base de datos para la autenticación de Windows &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Usar certificados para un punto de conexión de creación de reflejo de la base de datos &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   [Especificar la dirección URL del punto de conexión al agregar o modificar una réplica de disponibilidad &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/specify endpoint url - adding or modifying availability replica.md)  
  
 **Para solucionar problemas de configuración de grupos de disponibilidad AlwaysOn**  
  
-   [Solucionar problemas de configuración de grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [Solucionar problemas relativos a una operación de agregar archivos con error &#40;grupos de disponibilidad AlwaysOn&#41;](../../../database-engine/availability-groups/windows/troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="RelatedContent"></a> Contenido relacionado  
  
-   **Blogs:**  
  
     [Always On - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases (Series de aprendizaje de AlwaysON - HADRON: uso del grupo de trabajo para las bases de datos compatibles con HADRON)](http://blogs.msdn.com/b/psssql/archive/2012/05/17/Always%20On-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [Blogs del equipo de AlwaysOn de SQL Server: blog oficial del equipo de AlwaysOn de SQL Server](http://blogs.msdn.com/b/sqlAlways%20On/)  
  
     [Blogs de los ingenieros de SQL Server de CSS](http://blogs.msdn.com/b/psssql/)  
  
-   **Vídeos:**  
  
     [Microsoft SQL Server Code-Named "Denali", Serie AlwaysOn, parte 1: Introducción a la solución de alta disponibilidad de próxima generación](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server Code-Named "Denali", Serie AlwaysOn, parte 2: Crear una solución esencial de alta disponibilidad mediante AlwaysOn](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Notas del producto:**  
  
     [Guía de soluciones AlwaysOn de Microsoft SQL Server para lograr alta disponibilidad y recuperación ante desastres](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Notas del producto de Microsoft para SQL Server 2012](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Notas del producto del equipo de asesoramiento al cliente de SQL Server](http://sqlcat.com/)  
  
## Vea también  
 [El punto de conexión de creación de reflejo de la base de datos &#40;SQL Server&#41;](../../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [Información general de los grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Requisitos previos, restricciones y recomendaciones para Grupos de disponibilidad AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs, restrictions, recommendations - always on availability.md)  
  
  