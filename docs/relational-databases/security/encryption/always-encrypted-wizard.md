---
title: Asistente de Siempre cifrado | Microsoft Docs
ms.custom: 
ms.date: 05/04/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: security
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.alwaysencryptedwizard.encryption.f1
- sql13.swb.alwaysencryptedwizard.f1
- sql.swb.alwaysencryptedwizard.masterkey.f1
helpviewer_keywords:
- Wizard, Always Encrypted
ms.assetid: 68daddc9-ce48-49aa-917f-6dec86ad5af5
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 8d07fe91f365bd274d835d77b22efb8830d09b70
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="always-encrypted-wizard"></a>Asistente para Always Encrypted
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

<a name="use-the-always-encrypted-wizard-to-help-protect-sensitive-data--stored-in-a-sql-server-database-always-encrypted-allows-clients-to-encrypt-sensitive-data-inside-client-applications-and-never-reveal-the-encryption-keys-to-sql-server-as-a-result-always-encrypted-provides-a-separation-between-those-who-own-the-data-and-can-view-it-and-those-who-manage-the-data-but-should-have-no-access--for-a-full-description-of-the-feature-see-always-encrypted-40database-engine41relational-databasessecurityencryptionalways-encrypted-database-enginemd"></a>Use el **Asistente para Always Encrypted** para ayudar a proteger los datos confidenciales almacenados en una base de datos de SQL Server. Always Encrypted permite a los clientes cifrar datos confidenciales en aplicaciones de cliente y nunca revelar las claves de cifrado en SQL Server. Como resultado, Always Encrypted proporciona una separación entre aquellos que poseen los datos (y pueden verlos) y aquellos que los administran (pero que no deberían tener acceso).  Para obtener una descripción completa de la característica, vea [Always Encrypted &#40;motor de base de datos&#41;](../../../relational-databases/security/encryption/always-encrypted-database-engine.md).  
 -  
 - Para ver un tutorial completo en el que se muestra cómo configurar Always Encrypted con el asistente y cómo usarlo en una aplicación cliente, vea [SQL Database tutorial: Protect sensitive data with Always Encrypted (Tutorial de Base de datos SQL: proteger información confidencial con Always Encrypted)](https://azure.microsoft.com/documentation/articles/sql-database-always-encrypted/).  
 -  
 - Para ver un vídeo que incluye el uso del asistente, vea [Keeping Sensitive Data Secure with Always Encrypted](https://channel9.msdn.com/events/DataDriven/SQLServer2016/AlwaysEncrypted)(Protección de la información confidencial con Always Encrypted). Consulte también el blog del equipo de seguridad de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [SSMS Encryption Wizard - Enabling Always Encrypted in a Few Easy Steps (Asistente para cifrado de SSMS: habilitación de Always Encrypted en unos sencillos pasos)](http://blogs.msdn.com/b/sqlsecurity/archive/2015/11/01/ssms-encryption-wizard-enabling-always-encrypted-made-easy.aspx).  
 -  
 - **Permisos:** para consultar columnas cifradas y seleccionar claves mediante este asistente, debe tener los permisos `VIEW ANY COLUMN MASTER KEY DEFINITION` y `VIEW ANY COLUMN ENCRYPTION KEY DEFINITION` . Para crear nuevas claves, además debe tener los permisos `ALTER ANY COLUMN MASTER KEY` y `ALTER ANY COLUMN ENCRYPTION KEY` .  
 -  
 -#### Para abrir el Asistente para Always Encrypted  
 -  
 -1.  Conéctese a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] con el componente del Explorador de objetos de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
 -  
 -2.  Haga clic con el botón derecho en la base de datos, seleccione **Tareas**y, luego, haga clic en **Cifrar columnas**.  
 -  
 -#### Página de selección de columnas  
 - Busque una tabla y una columna y, después, seleccione un tipo de cifrado (determinista o aleatorio) y una clave de cifrado para las columnas seleccionadas. Para descifrar una columna que actualmente está cifrada, seleccione **Plaintext**(Texto simple). Para girar una clave de cifrado de columna, seleccione una clave de cifrado diferente y el asistente descifrará la columna y la volverá a cifrar con la clave nueva. (El cifrado de tablas temporales y en memoria es compatible con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , pero no se puede configurar mediante este asistente).  
 -  
 -#### Página de configuración de la clave maestra  
 - Cree una nueva clave maestra de columna en el Almacén de certificados de Windows o en el Almacén de claves de Azure. Para obtener más información, consulte los vínculos indicados más abajo en la sección Almacenamiento de claves.  
 -  
 - Si ha elegido una clave de cifrado de columna generada automáticamente en la página de selección de columnas, debe configurar una clave maestra de columna con la que se cifrará la clave de cifrado de columna generada. Si ya tiene una clave maestra de columna definida en la base de datos, puede seleccionarla. (Para usar una clave maestra de columna existente, el usuario debe tener permiso para tener acceso a la clave). También puede generar una clave maestra de columna en un almacén de claves seleccionado (Almacén de certificados de Windows o Almacén de claves de Azure) y definir la clave en la base de datos.  
 -  
 - **Almacenamiento de claves**  
 -  
 - Elija el lugar en el que se almacenará la clave maestra de columna.  
 -  
 --   **Almacenar una clave maestra en certificados de Windows** Para más información, vea [Using Certificate Stores](https://msdn.microsoft.com/library/windows/desktop/aa388160.aspx) (Uso de almacenes de certificados)  
 -  
 --   **Almacenar una clave maestra en el Almacén de claves de Azure** Para más información, vea [Introducción a Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-get-started/).  
 -  
 - Para generar una clave maestra de columna en el Almacén de claves de Azure, el usuario debe tener los permisos **WrapKey**, **UnwrapKey**, **Verify**y **Sign** para el almacén de claves. Los usuarios también podrían necesitar los permisos **Get**, **List**, **Create**, **Delete**, **Update**, **Import**, **Backup**y **Restore** . Para obtener más información, vea [¿Qué es el Almacén de claves de Azure?](https://azure.microsoft.com/documentation/articles/key-vault-whatis/) y   [Set-AzureRmKeyVaultAccessPolicy](https://msdn.microsoft.com/library/mt603625.aspx).  
 -  
 - El asistente solo admite dos opciones. Los módulos de seguridad de hardware y los almacenes de cliente deben configurarse mediante [CREATE COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/create-column-master-key-transact-sql.md)[!INCLUDE[tsql](../../../includes/tsql-md.md)].  
 -  
 -## Términos de Always Encrypted  
 -  
 El --   **cifrado determinista** usa un método que genera siempre el mismo valor cifrado para cualquier valor de texto no cifrado concreto. El uso del cifrado determinista permite la agrupación, el filtrado por igualdad y la unión de tablas según los valores cifrados; sin embargo, también puede permitir que usuarios no autorizados averigüen la información de los valores cifrados examinando los patrones de la columna cifrada. Este punto débil aumenta cuando hay un conjunto pequeño de posibles valores cifrados, como verdadero/falso o región norte/sur/este/oeste. El cifrado determinista debe usar una intercalación de columna con un criterio de ordenación binario 2 para columnas de caracteres.  
 -  
 El --   **cifrado aleatorio** usa un método que cifra los datos de una manera menos predecible. El cifrado aleatorio es más seguro, pero impide las búsquedas de igualdad, agrupación, indexación y la unión en columnas cifradas.  
 -  
 Las --   **claves maestras de columna** protegen las claves usadas para cifrar las claves de cifrado de columna. Las claves maestras de columna deben almacenarse en un almacén de claves de confianza. La información sobre claves maestras de columna, incluida su ubicación, se almacena en la base de datos de las vistas de catálogo del sistema.  
 -  
 Las --   **claves de cifrado de columna** se usan para cifrar la información confidencial almacenada en las columnas de la base de datos. Todos los valores de una columna se pueden cifrar mediante una clave de cifrado de columna única. Los valores cifrados de las claves de cifrado de columna se almacenan en la base de datos de vistas de catálogo del sistema. Debe almacenar las claves de cifrado de columna en una ubicación segura o de confianza como copia de seguridad.  
 -  
 -## Vea también  
 - [Always Encrypted &#40;motor de base de datos&#41;](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
 - [Administración extensible de claves con el Almacén de claves de Azure &#40;SQL Server&#41;](../../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
