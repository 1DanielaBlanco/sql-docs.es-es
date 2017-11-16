---
title: "Inicialización instantánea de archivos de la base de datos | Microsoft Docs"
ms.custom: 
ms.date: 08/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- initializing files [SQL Server]
- instant file initializations [SQL Server]
- fast file initialization (SQL Server)
- file initialization [SQL Server]
ms.assetid: 1ad468f5-4f75-480b-aac6-0b01b048bd67
caps.latest.revision: "33"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 5d1ed7065cdbf710888c6b455fc1a059ecaebbfe
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="database-instant-file-initialization"></a>Inicialización instantánea de archivos de la base de datos
  Los archivos de datos y registro se inicializan para sobrescribir los datos existentes que los archivos eliminados anteriormente hayan dejado en el disco. Los archivos de datos y registro se inicializan por primera vez rellenando los archivos con ceros al realizar una de las siguientes operaciones:  
  
-   Crear una base de datos.  
  
-   Agregue archivos de registro o datos a una base de datos existente.  
  
-   Aumentar el tamaño de un archivo existente (incluidas las operaciones de crecimiento automático).  
  
-   Restaurar una base de datos o un grupo de archivos.  
  
 Inicializar los archivos hace que estas operaciones tarden más. Sin embargo, cuando los datos se escriben en los archivos por primera vez, el sistema operativo no tiene que rellenar los archivos con ceros.  
  
## <a name="instant-file-initialization"></a>Inicialización instantánea de archivos  
 En [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], los archivos de datos se pueden inicializar de forma instantánea. La inicialización instantánea de archivos le permite ejecutar rápidamente las operaciones con archivos mencionadas anteriormente. La inicialización instantánea de archivos recupera espacio en disco utilizado sin rellenarlo con ceros. En lugar de eso, el contenido del disco se sobrescribe al escribir nuevos datos en los archivos. Los archivos de registro no se pueden inicializar de forma instantánea.  
  
> [!NOTE]  
>  La inicialización instantánea de archivos solo está disponible en [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[winxppro](../../includes/winxppro-md.md)] , [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] o en versiones posteriores.  
  
 La inicialización instantánea de archivos solo está disponible si a la cuenta de servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) se le ha concedido SE_MANAGE_VOLUME_NAME. Los miembros del grupo de administradores de Windows tienen este derecho y pueden concederlo a otros usuarios añadiéndolos a la directiva de seguridad **Realizar tareas de mantenimiento del volumen** . Para obtener más información sobre la asignación de derechos de usuario, consulte la documentación de Windows.  
  
Algunas condiciones, como TDE, pueden evitar la inicialización instantánea de archivos.  
  
 Para conceder a una cuenta el permiso `Perform volume maintenance tasks` :  
  
1.  En el equipo en el que se creará el archivo de copia de seguridad, abra la aplicación **Directiva de seguridad local** (`secpol.msc`).  
  
2.  En el panel izquierdo, expanda **Directivas locales**y, a continuación, haga clic en **Asignación de derechos de usuario**.  
  
3.  En el panel derecho, haga doble clic en **Realizar tareas de mantenimiento del volumen**.  
  
4.  Haga clic en **Agregar usuario o grupo** y añada las cuentas de usuario que se utilicen para las copias de seguridad.  
  
5.  Haga clic en **Aplicar**y, a continuación, cierre todos los cuadros de diálogo de **Directiva de seguridad local** .  
  
### <a name="security-considerations"></a>Consideraciones de seguridad  
 Como el contenido del disco eliminado solo se sobrescribe cuando se escriben nuevos datos a los archivos, una entidad de seguridad no autorizada puede acceder al contenido eliminado. Mientras el archivo de la base de datos se adjunte a la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], esta amenaza de divulgación de la información se reduce mediante la lista de control de acceso discrecional (DACL) del archivo. Esta DACL permite acceder al archivo solo a la cuenta de servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y al administrador local. Sin embargo, cuando el archivo está separado, un usuario o servicio que no tenga SE_MANAGE_VOLUME_NAME puede acceder a él. Existe una amenaza parecida al crear una copia de seguridad de la base de datos. Si el archivo de copia de seguridad no está protegido con una DACL adecuada, el contenido eliminado puede estar disponible para un usuario o servicio no autorizado.  
  
 Si le preocupa la posibilidad de que se divulgue contenido eliminado, realice una de las acciones siguientes o ambas:  
  
-   Asegúrese siempre de que los archivos separados y los archivos de copia de seguridad tienen DACL restrictivas.  
  
-   Deshabilite la inicialización instantánea de archivos para la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] revocando SE_MANAGE_VOLUME_NAME de la cuenta de servicio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  Deshabilitar la inicialización instantánea de archivos solo afecta a los archivos que se han creado o se ha aumentado su tamaño después de que el derecho del usuario se revocara.  
  
## <a name="see-also"></a>Vea también  
 [CREATE DATABASE &#40;Transact-SQL de SQL Server&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)  
  
  
