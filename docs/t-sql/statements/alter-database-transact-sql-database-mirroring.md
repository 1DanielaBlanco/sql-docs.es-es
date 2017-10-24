---
title: "ALTER (Transact-SQL) de creación de reflejo de base de datos de base de datos | Documentos de Microsoft"
ms.custom: 
ms.date: 08/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- witness [SQL Server], establishing
- manual failover [SQL Server]
- ALTER DATABASE statement, database mirroring
- database mirroring [SQL Server], Transact-SQL
ms.assetid: 27a032ef-1cf6-4959-8e67-03d28c4b3465
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 96ac469df9660e29c0394226cf7199e451df9d8c
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-transact-sql-database-mirroring"></a>Base de datos de ALTER DATABASE (Transact-SQL) de creación de reflejo 
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Use [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] en su lugar.  
  
 Controla la creación de reflejo de la base de datos. Los valores especificados con las opciones de creación de reflejo de la base de datos se aplican a las dos copias de la base de datos y a la sesión de creación de reflejo de la base de datos en conjunto. Solo un \<database_mirroring_option > se permite por instrucción ALTER DATABASE.  
  
> [!NOTE]  
>  Se recomienda que configuran la duplicación de base de datos durante las horas, porque la configuración puede afectar al rendimiento.  
  
 Para obtener opciones de ALTER DATABASE, consulte [ALTER DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql.md). Para opciones de ALTER DATABASE SET, vea [ALTER DATABASE SET Options &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
ALTER DATABASE database_name   
SET { <partner_option> | <witness_option> }  
  <partner_option> ::=  
    PARTNER { = 'partner_server'   
            | FAILOVER   
            | FORCE_SERVICE_ALLOW_DATA_LOSS  
            | OFF  
            | RESUME   
            | SAFETY { FULL | OFF }  
            | SUSPEND   
            | TIMEOUT integer  
            }  
  <witness_option> ::=  
    WITNESS { = 'witness_server'   
            | OFF   
            }  
  
```  
  
## <a name="arguments"></a>Argumentos  
  
> [!IMPORTANT]  
>  Un comando SET PARTNER o SET WITNESS puede completarse correctamente cuando se escribe y, sin embargo, provocar un error más adelante.  
  
> [!NOTE]  
>  Las opciones de creación de reflejo de la base de datos de ALTER DATABASE no están disponibles para una base de datos independiente.  
  
 *database_name*  
 Es el nombre de la base de datos que se va a modificar.  
  
 Socio comercial \<partner_option >  
 Controla las propiedades de la base de datos que definen los asociados de conmutación por error de una sesión de creación de reflejo de la base de datos y su comportamiento. Algunas opciones de SET PARTNER se pueden establecer en cualquier asociado; otras opciones se limitan al servidor principal o al servidor reflejado. Para obtener más información, vea las opciones de PARTNER especificadas a continuación. Una cláusula SET PARTNER afecta a ambas copias de la base de datos, con independencia del asociado en el que se especifica.  
  
 Para ejecutar una instrucción SET PARTNER, el valor de STATE de los extremos de ambos asociados debe ser STARTED. Además, debe tener en cuenta que el valor de ROLE del extremo de la creación de reflejo de la base de datos de cada instancia del servidor asociado debe establecerse en PARTNER o ALL. Para obtener información sobre cómo especificar un punto de conexión, vea [crear una base de datos de creación de reflejo de punto de conexión de autenticación de Windows &#40; Transact-SQL &#41; ](../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md). Para conocer el rol y el estado del extremo de la creación de reflejo de la base de datos de una instancia del servidor, debe usar la siguiente instrucción de [!INCLUDE[tsql](../../includes/tsql-md.md)] en dicha instancia:  
  
```  
SELECT role_desc, state_desc FROM sys.database_mirroring_endpoints  
```  
  
 **\<partner_option >:: =**  
  
> [!NOTE]  
>  Solo un \<partner_option > se permite por cada cláusula SET PARTNER.  
  
 **'** *partner_server* **'**  
 Especifica la dirección de red del servidor de una instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] para actuar como un asociado de conmutación por error en la nueva sesión de creación de reflejo de la base de datos. Cada sesión requiere dos asociados: uno empieza como servidor principal y el otro como servidor reflejado. Se recomienda que estos asociados residan en equipos distintos.  
  
 Esta opción se especifica una vez por sesión en cada asociado. Iniciar una sesión de creación de reflejo de la base de datos requiere dos ALTER DATABASE *base de datos* SET PARTNER **='***partner_server***'** instrucciones . El orden es relevante. En primer lugar, conéctese al servidor reflejado y especifique la instancia de servidor principal como *partner_server* (SET PARTNER **='***principal_server***'**). En segundo lugar, conéctese al servidor principal y especificar la instancia del servidor reflejado como *partner_server* (SET PARTNER **='***mirror_server***'**); Esto inicia una sesión entre estos dos asociados de creación de reflejo de la base de datos. Para obtener más información, vea [Configurar la creación de reflejo de la base de datos &#40;SQL Server&#41;](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md).  
  
 El valor de *partner_server* es una dirección de red de servidor. Tiene la siguiente sintaxis:  
  
 TCP**://***\<dirección del sistema>***:***\<puerto>*  
  
 donde  
  
-   *\<dirección del sistema >* es una cadena, como un nombre de sistema, un nombre de dominio completo o una dirección IP, que identifica de forma inequívoca el sistema del equipo de destino.  
  
-   *\<puerto >* es un número de puerto que está asociado con el extremo de reflejo de la instancia de servidor asociado.  
  
 Para obtener más información, vea [Especificar una dirección de red de servidor &#40;creación de reflejo de la base de datos&#41;](../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md).  
  
 En el ejemplo siguiente se muestra la SET PARTNER **='***partner_server***'** cláusula:  
  
```  
'TCP://MYSERVER.mydomain.Adventure-Works.com:7777'  
```  
  
> [!IMPORTANT]  
>  Si se configura una sesión con la instrucción ALTER DATABASE en lugar de con [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], se establece de forma predeterminada con la seguridad de transacciones completa (SAFETY se establece en FULL) y se ejecuta en el modo de alta seguridad sin conmutación automática por error. Para permitir la conmutación automática por error, se debe configurar un testigo; para ejecutar en modo de alto rendimiento, se debe desactivar la seguridad de transacciones (SAFETY OFF).  
  
 FAILOVER  
 Conmuta manualmente el servidor principal al servidor reflejado. Solo puede especificar FAILOVER en el servidor principal. Esta opción es válida solo si la configuración de SAFETY es FULL (valor predeterminado).  
  
 La opción de conmutación por error requiere **maestro** como el contexto de base de datos.  
  
 FORCE_SERVICE_ALLOW_DATA_LOSS  
 Fuerza la aplicación del servicio de base de datos a la base de datos reflejada si se produce un error en el servidor principal con la base de datos en un estado no sincronizado o en un estado sincronizado cuando no se produce la conmutación automática por error.  
  
 Se recomienda que el servicio solo se fuerce si el servidor principal ya no se está ejecutando. En caso contrario, es posible que algunos clientes sigan teniendo acceso a la base de datos principal original en lugar de a la base de datos principal nueva.  
  
 FORCE_SERVICE_ALLOW_DATA_LOSS está disponible solo en el servidor reflejado y si se cumplen todas las condiciones siguientes:  
  
-   El servidor principal está inactivo.  
  
-   WITNESS está establecido en OFF o el testigo está conectado al servidor reflejado.  
  
 Fuerce el servicio solo si es aceptable el riesgo de perder datos para restaurar el servicio en la base de datos inmediatamente.  
  
 Al forzar el servicio, se suspende la sesión, lo que conserva temporalmente todos los datos de la base de datos principal original. Una vez que el servidor principal original esté en funcionamiento y pueda comunicarse con el nuevo servidor principal, el administrador de la base de datos podrá reanudar el servicio. Cuando se reanuda la sesión, se pierden los registros no enviados y las actualizaciones correspondientes.  
  
 OFF  
 Quita una sesión de creación de reflejo de la base de datos, así como los reflejos de la base de datos. Puede especificar OFF en cualquier asociado. Para obtener información, sobre el impacto de quitar la creación de reflejo, vea [quitar creación de reflejo de base de datos &#40; SQL Server &#41; ](../../database-engine/database-mirroring/removing-database-mirroring-sql-server.md).  
  
 RESUME  
 Reanuda la sesión de creación de reflejo de la base de datos suspendida. Solo puede especificar RESUME en el servidor principal.  
  
 SAFETY { FULL | OFF }  
 Establece el nivel de seguridad de las transacciones. Solo puede especificar SAFETY en el servidor principal.  
  
 El valor predeterminado es FULL. Con la seguridad completa, la sesión de creación de reflejo de la base de datos se ejecuta sincrónicamente (en *modo de alta seguridad*). Si la seguridad está configurada en OFF, la sesión de creación de reflejo de la base de datos se ejecuta de forma asincrónica (en *modo de alto rendimiento*).  
  
 El comportamiento del modo de alta seguridad depende en parte del testigo, como se indica a continuación:  
  
-   Si la seguridad se establece en FULL y se establece el testigo para la sesión, dicha sesión se ejecuta en el modo de alta seguridad con conmutación automática por error. Si se pierde la conexión con el servidor principal, se produce automáticamente la conmutación por error de la sesión si la base de datos está sincronizada y la instancia del servidor reflejado y el testigo siguen conectados entre sí (es decir, tienen quórum). Para obtener más información, vea [Cuórum: cómo un testigo afecta a la disponibilidad de la base de datos &#40;reflejo de la base de datos&#41;](../../database-engine/database-mirroring/quorum-how-a-witness-affects-database-availability-database-mirroring.md).  
  
     Si se establece un testigo para la sesión, pero está desconectado actualmente, la pérdida del servidor reflejado causa el bloqueo del servidor principal.  
  
-   Si la seguridad se establece en FULL y el testigo en OFF, dicha sesión se ejecuta en el modo de alta seguridad sin conmutación automática por error. Si la instancia del servidor reflejado se bloquea, la instancia del servidor principal no se ve afectada. Si la instancia del servidor principal se bloquea, se puede forzar el servicio (con una posible pérdida de datos) en la instancia del servidor reflejado.  
  
 Si SAFETY se establece en OFF, la sesión se ejecuta en el modo de alto rendimiento y no se admite la conmutación automática o manual por error. Sin embargo, los problemas del servidor reflejado no afectan al servidor principal y, si la instancia de este se bloquea, puede forzar el servicio si es necesario (con una posible pérdida de datos) en la instancia del servidor reflejado, siempre que WITNESS esté establecido en OFF o el testigo esté conectado actualmente al reflejo. Para obtener más información acerca de cómo forzar la aplicación del servicio, vea "FORCE_SERVICE_ALLOW_DATA_LOSS" en un apartado anterior de esta sección.  
  
> [!IMPORTANT]  
>  El modo de alto rendimiento no se ha diseñado para que use un testigo. Sin embargo, siempre que se establece SAFETY en OFF, es muy recomendable asegurarse de que WITNESS está establecido en OFF.  
  
 SUSPEND  
 Pausa una sesión de creación de reflejo de la base de datos.  
  
 Puede especificar SUSPEND en cualquier asociado.  
  
 Tiempo de espera *entero*  
 Especifica el período de espera en segundos. El período de espera es el tiempo máximo durante el que una instancia de servidor espera hasta recibir un mensaje PING de otra instancia en la sesión de creación de reflejo de la base de datos, antes de considerar que la otra instancia está desconectada.  
  
 Solo puede especificar la opción TIMEOUT en el servidor principal. Si no especifica esta opción, el período equivale a 10 segundos de forma predeterminada. Si especifica 5 o más, el tiempo de espera se establece en el número de segundos especificado. Si especifica un tiempo de espera de 0 a 4 segundos, dicho tiempo de espera se establece automáticamente en 5 segundos.  
  
> [!IMPORTANT]  
>  Es recomendable que mantenga el período de espera en 10 segundos o más. Si establece el valor en menos de 10 segundos, existe la posibilidad de que un sistema sobrecargado no reciba los PING y declare un error falso.  
  
 Para más información, consulte [Possible Failures During Database Mirroring](../../database-engine/database-mirroring/possible-failures-during-database-mirroring.md).  
  
 TESTIGO \<witness_option >  
 Controla las propiedades de base de datos que definen un testigo de creación de reflejo de la base de datos. La cláusula SET WITNESS afecta a ambas copias de la base de datos, pero solo puede especificar SET WITNESS en el servidor principal. Si se establece un testigo para una sesión, se requiere quórum para servir la base de datos, independientemente de la configuración de seguridad; Para obtener más información, consulte [quórum: cómo un testigo afecta a la base de datos de disponibilidad &#40; creación de reflejo de base de datos &#41;](../../database-engine/database-mirroring/quorum-how-a-witness-affects-database-availability-database-mirroring.md).  
  
 Se recomienda que el testigo y los asociados de conmutación por error residan en equipos distintos. Para obtener información acerca del testigo, vea [testigo de creación de reflejo de base de datos](../../database-engine/database-mirroring/database-mirroring-witness.md).  
  
 Para ejecutar una instrucción SET WITNESS, el valor de STATE de los extremos de las instancias del servidor principal y del servidor testigo debe establecerse en STARTED. Además, debe tener en cuenta que el valor de ROLE del extremo de creación de reflejo de la base de datos de una instancia del servidor testigo debe establecerse en WITNESS u ALL. Para obtener información acerca de cómo especificar un punto de conexión, vea [extremo de creación de reflejo de la base de datos &#40; SQL Server &#41; ](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md).  
  
 Para conocer el rol y el estado del extremo de la creación de reflejo de la base de datos de una instancia del servidor, debe usar la siguiente instrucción de [!INCLUDE[tsql](../../includes/tsql-md.md)] en dicha instancia:  
  
```  
SELECT role_desc, state_desc FROM sys.database_mirroring_endpoints  
```  
  
> [!NOTE]  
>  Las propiedades de base de datos no se pueden establecer en el testigo.  
  
 **\<witness_option >:: =**  
  
> [!NOTE]  
>  Solo un \<witness_option > se permite por cada cláusula SET WITNESS.  
  
 **'** *servidor_testigo* **'**  
 Especifica una instancia del [!INCLUDE[ssDE](../../includes/ssde-md.md)] para que actúe como el servidor testigo para una sesión de creación de reflejo de la base de datos. Solo puede especificar instrucciones SET WITNESS en el servidor principal.  
  
 En un SET WITNESS **='***servidor_testigo***'** instrucción, la sintaxis de *servidor_testigo* es igual que la sintaxis de  *partner_server*.  
  
 OFF  
 Quita el testigo de la sesión de creación de reflejo de la base de datos. Si se establece el testigo en OFF, se deshabilita la conmutación automática por error. Si la base de datos se establece en FULL SAFETY y el testigo se establece en OFF, un error del servidor reflejado hace que el servidor principal anule la disponibilidad de la base de datos.  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-creating-a-database-mirroring-session-with-a-witness"></a>A. Crear una sesión de creación de reflejo de la base de datos con un testigo  
 La configuración de la creación de reflejo de la base de datos con un testigo requiere configurar la seguridad y preparar la base de datos reflejada, además de usar ALTER DATABASE para configurar los asociados. Para obtener un ejemplo del proceso de completar la instalación, consulte [configuración de la base de datos de creación de reflejo &#40; SQL Server &#41; ](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md).  
  
### <a name="b-manually-failing-over-a-database-mirroring-session"></a>B. Conmutación manual por error en una sesión de creación de reflejo de la base de datos  
 La conmutación manual por error se puede iniciar desde cualquier asociado de creación de reflejo de la base de datos. Antes de llevar a cabo la conmutación por error, debe comprobar si el servidor principal actual es realmente el servidor principal. Por ejemplo, para la base de datos [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], ejecute la siguiente consulta en la instancia del servidor que crea que es el servidor principal actual:  
  
```  
SELECT db.name, m.mirroring_role_desc   
FROM sys.database_mirroring m   
JOIN sys.databases db  
ON db.database_id = m.database_id  
WHERE db.name = N'AdventureWorks2012';   
GO  
```  
  
 Si la instancia del servidor es la entidad de seguridad, el valor de `mirroring_role_desc` es `Principal`. Si esta instancia del servidor se corresponde con el servidor reflejado, la instrucción `SELECT` debe devolver `Mirror`.  
  
 En el siguiente ejemplo se da por supuesto que el servidor es la entidad de seguridad actual.  
  
1.  Realice una conmutación manual por error al asociado de creación de reflejo de la base de datos:  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER FAILOVER;  
    GO  
    ```  
  
2.  Para comprobar los resultados de la conmutación por error en el reflejo nuevo, ejecute la siguiente consulta:  
  
    ```  
    SELECT db.name, m.mirroring_role_desc   
    FROM sys.database_mirroring m   
    JOIN sys.databases db  
    ON db.database_id = m.database_id  
    WHERE db.name = N'AdventureWorks2012';   
    GO  
    ```  
  
     El valor actual de `mirroring_role_desc` es ahora `Mirror`.  
  
## <a name="see-also"></a>Vea también  
 [CREATE DATABASE &#40;Transact-SQL de SQL Server&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [Sys.database_mirroring_witnesses &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)  
  
  

