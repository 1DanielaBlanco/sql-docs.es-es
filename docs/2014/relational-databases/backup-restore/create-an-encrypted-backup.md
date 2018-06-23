---
title: Creación de una copia de seguridad cifrada | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e29061d3-c2ab-4d98-b9be-8e90a11d17fe
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3cd11409f4194e6eaa63c03d4ca211fe633a721a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36201395"
---
# <a name="create-an-encrypted-backup"></a>Crear una copia de seguridad cifrada
  En este tema se describen los pasos necesarios para crear una copia de seguridad cifrada mediante Transact-SQL.  
  
## <a name="backup-to-disk-with-encryption"></a>Copia de seguridad en disco con cifrado  
 **Requisitos previos:**  
  
-   Acceso a un disco local o al almacenamiento con espacio suficiente para crear una copia de seguridad de la base de datos.  
  
-   Una clave maestra de base de datos para la base de datos maestra y un certificado o una clave asimétrica disponible en la instancia de SQL Server. Para conocer los requisitos de cifrado y los permisos, vea [Backup Encryption](backup-encryption.md).  
  
 Siga estos pasos para crear una copia de seguridad cifrada de una base de datos en un disco local. En este ejemplo se utiliza una base de datos de usuario denominada MyTestDB.  
  
1.  **Cree una clave maestra de base de datos de la base de datos maestra:** elija una contraseña para cifrar la copia de la clave maestra que se almacenará en la base de datos. Conecte con el motor de base de datos, inicie una nueva ventana de consulta, copie y pegue el siguiente ejemplo y haga clic en **Ejecutar**.  
  
    ```  
    -- Creates a database master key.   
    -- The key is encrypted using the password "<master key password>"  
    USE master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
2.  **Cree un certificado de copia de seguridad:** cree un certificado de copia de seguridad en la base de datos maestra. Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**.  
  
    ```  
    Use Master  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDB Backup Encryption Certificate';  
    GO  
  
    ```  
  
3.  **Haga una copia de seguridad de la base de datos:** especifique el algoritmo de cifrado y el certificado que se usará. Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**.  
  
    ```  
    BACKUP DATABASE [MyTestDB]  
    TO DISK = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
    WITH  
      COMPRESSION,  
      ENCRYPTION   
       (  
       ALGORITHM = AES_256,  
       SERVER CERTIFICATE = MyTestDBBackupEncryptCert  
       ),  
      STATS = 10  
    GO  
  
    ```  
  
 Para obtener un ejemplo sobre cómo cifrar una copia de seguridad protegida por EKM, vea [Administración extensible de claves con el Almacén de claves de Azure &#40;SQL Server&#41;](../security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md).  
  
### <a name="backup-to-windows-azure-storage-with-encryption"></a>Copia de seguridad en Almacenamiento de Windows Azure con cifrado  
 Si crea una copia de seguridad en Almacenamiento de Windows Azure con la opción **Copia de seguridad en URL de SQL Server** , los pasos de cifrado son los mismos pero debe usar una dirección URL como destino y una credencial SQL para autenticarse en Almacenamiento de Windows Azure. Si desea configurar [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] con opciones de cifrado, vea [configurar SQL Server Managed Backup to Windows Azure](enable-sql-server-managed-backup-to-microsoft-azure.md) y [configuración de SQL Server Managed Backup to Windows Azure para grupos de disponibilidad](../../database-engine/setting-up-sql-server-managed-backup-to-windows-azure-for-availability-groups.md).  
  
 **Requisitos previos:**  
  
-   Una cuenta de almacenamiento de Windows y un contenedor. Para obtener más información, vea: Columnas en la tabla de origen capturadas[Lesson 1: Create Windows Azure Storage Objects](../../tutorials/lesson-1-create-windows-azure-storage-objects.md)  
  
-   Una clave maestra para la base de datos maestra y un certificado o una clave asimétrica en la instancia de SQL Server. Para conocer los requisitos de cifrado y los permisos, vea [Backup Encryption](backup-encryption.md).  
  
1.  **Cree la credencial de SQL Server:** para crear una credencial de SQL Server, conecte con el motor de base de datos, abra una nueva ventana de consulta, copie y pegue el ejemplo siguiente y haga clic en **Ejecutar**.  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' – this is the name of the storage account you specified when creating a storage account    
    , SECRET = '<storage account access key>' – this should be either the Primary or Secondary Access Key for the storage account  
    ```  
  
2.  **Cree una clave maestra de base de datos:** elija una contraseña para cifrar la copia de la clave maestra que se almacenará en la base de datos. Conecte con el motor de base de datos, inicie una nueva ventana de consulta, copie y pegue el siguiente ejemplo y haga clic en **Ejecutar**.  
  
    ```  
    -- Creates a database master key.  
    -- The key is encrypted using the password "<master key password>"  
    USE Master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<master key password>';  
    GO  
  
    ```  
  
3.  **Cree un certificado de copia de seguridad:** cree un certificado de copia de seguridad en la base de datos maestra. Copie el ejemplo siguiente, péguelo en la ventana de consulta y haga clic en **Ejecutar**.  
  
    ```  
    USE Master;  
    GO  
    CREATE CERTIFICATE MyTestDBBackupEncryptCert  
       WITH SUBJECT = 'MyTestDBBackupEncryptCert ';  
    GO  
  
    ```  
  
4.  **Haga una copia de seguridad de la base de datos:** especifique el algoritmo de cifrado y el certificado que se usará. Copie y pegue el siguiente ejemplo en la ventana de consulta y haga clic en **Ejecutar**.  
  
    ```  
    BACKUP DATABASE [MyTestDB]  
    TO URL = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Backup\MyTestDB.bak'  
    WITH  
      CREDENTIAL 'mycredential' – this is the name of the credential created in the first step.  
      ,COMPRESSION  
      ,ENCRYPTION   
       (  
       ALGORITHM = AES_256,  
       SERVER CERTIFICATE = MyTestDBBackupEncryptCert  
       ),  
      STATS = 10  
    GO  
  
    ```  
  
  