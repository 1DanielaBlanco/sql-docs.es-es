---
title: 'Lección 1: Creación de una directiva de acceso almacenada y una firma de acceso compartido | Microsoft Docs'
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: tutorial
ms.reviewer: ''
ms.suite: sql
ms.technology: backup-restore
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
ms.assetid: 41674d9d-8132-4bff-be4d-85a861419f3d
caps.latest.revision: 22
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 721f9245ff8057c54cef5facdf4a4de423e53961
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-1-create-stored-access-policy-and-shared-access-signature"></a>Lección 1: Creación de una directiva de acceso almacenada y una firma de acceso compartido
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
En esta lección, usará un script de [PowerShell de Azure](https://azure.microsoft.com/en-us/documentation/articles/powershell-install-configure/) para crear una firma de acceso compartido en un contenedor de blobs de Azure mediante una directiva de acceso almacenada.  
  
> [!NOTE]  
> Este script se escribió con Azure PowerShell 5.0.10586.  
  
Una firma de acceso compartido es un URI que concede derechos de acceso restringidos a los contenedores, los blobs, las colas o las tablas. Una directiva de acceso almacenada proporciona un nivel de control adicional sobre las firmas de acceso compartidas en el servidor, incluida la revocación, expiración o ampliación del acceso. Al usar esta nueva mejora, debe crear una directiva en un contenedor con derechos de lectura, escritura y enumeración como mínimo.  
  
Puede crear una directiva de acceso y una firma de acceso compartido mediante PowerShell de Azure, el SDK Azure Storage, la API de REST de Azure o una utilidad de terceros. Este tutorial muestra cómo usar un script de PowerShell de Azure para completar esta tarea. El script usa el modelo de implementación del Administrador de recursos y crea los siguientes  recursos nuevos  
  
-   Grupo de recursos  
  
-   Cuenta de almacenamiento  
  
-   Contenedor de blobs de Azure  
  
-   Directiva SAS  
  
Este script comienza con la declaración de una serie de variables para especificar los nombres para los recursos anteriores y los nombres para los siguientes valores de entrada necesarios:  
  
-   El nombre de prefijo usado en la nomenclatura de otros objetos de recursos  
  
-   Nombre de suscripción  
  
-   Ubicación del centro de datos  
  
> [!NOTE]  
> Este script se escribe de manera que pueda usar recursos de modelo de implementación ARM o clásicos existentes.  
  
El script termina con la generación de la instrucción CREATE CREDENTIAL correspondiente que se va a usar en la [Lección 2: Crear una credencial de SQL Server con una firma de acceso compartido](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md). Esta instrucción se copia en el Portapapeles y se reproduce en la consola para que la pueda ver.  
  
Para crear una directiva en el contenedor y generar una clave de firma de acceso compartido (SAS), haga lo siguiente:  
  
1.  Abra la ventana de PowerShell o Windows PowerShell ISE (consulte los requisitos de versión anteriores).  
  
2.  Edite y ejecute el siguiente script.  
  
    ```  
    <#   
    This script uses the Azure Resource model and creates a new ARM storage account.  
    Modify this script to use an existing ARM or classic storage account   
    using the instructions in comments within this script  
    #>  
    # Define global variables for the script  
    $prefixName = '<a prefix name>'  # used as the prefix for the name for various objects  
    $subscriptionName='<your subscription name>'   # the name  of subscription name you will use  
    $locationName = '<a data center location>'  # the data center region you will use  
    $storageAccountName= $prefixName + 'storage' # the storage account name you will create or use  
    $containerName= $prefixName + 'container'  # the storage container name to which you will attach the SAS policy with its SAS token  
    $policyName = $prefixName + 'policy' # the name of the SAS policy  
  
    <#   
    Using Azure Resource Manager deployment model  
    Comment out this entire section and use the classic storage account name to use an existing classic storage account  
    #>  
  
    # Set a variable for the name of the resource group you will create or use  
    $resourceGroupName=$prefixName + 'rg'   
  
    # adds an authenticated Azure account for use in the session   
    Login-AzureRmAccount    
  
    # set the tenant, subscription and environment for use in the rest of   
    Set-AzureRmContext -SubscriptionName $subscriptionName   
  
    # create a new resource group - comment out this line to use an existing resource group  
    New-AzureRmResourceGroup -Name $resourceGroupName -Location $locationName   
  
    # Create a new ARM storage account - comment out this line to use an existing ARM storage account  
    New-AzureRmStorageAccount -Name $storageAccountName -ResourceGroupName $resourceGroupName -Type Standard_RAGRS -Location $locationName   
  
    # Get the access keys for the ARM storage account  
    $accountKeys = Get-AzureRmStorageAccountKey -ResourceGroupName $resourceGroupName -Name $storageAccountName  
  
    # Create a new storage account context using an ARM storage account  
    $storageContext = New-AzureStorageContext -StorageAccountName $storageAccountName -StorageAccountKey $accountKeys[0].Value 
  
    <#  
    Using the Classic deployment model  
    Use the following four lines to use an existing classic storage account  
    #>  
    #Classic storage account name  
    #Add-AzureAccount  
    #Select-AzureSubscription -SubscriptionName $subscriptionName #provide an existing classic storage account  
    #$accountKeys = Get-AzureStorageKey -StorageAccountName $storageAccountName  
    #$storageContext = New-AzureStorageContext -StorageAccountName $storageAccountName -StorageAccountKey $accountKeys.Primary  
  
    # The remainder of this script works with either the ARM or classic sections of code above  
  
    # Creates a new container in blob storage  
    $container = New-AzureStorageContainer -Context $storageContext -Name $containerName  
  
    # Sets up a Stored Access Policy and a Shared Access Signature for the new container  
    $policy = New-AzureStorageContainerStoredAccessPolicy -Container $containerName -Policy $policyName -Context $storageContext -StartTime $(Get-Date).ToUniversalTime().AddMinutes(-5) -ExpiryTime $(Get-Date).ToUniversalTime().AddYears(10) -Permission rwld

    # Gets the Shared Access Signature for the policy  
    $sas = New-AzureStorageContainerSASToken -name $containerName -Policy $policyName -Context $storageContext
    Write-Host 'Shared Access Signature= '$($sas.Substring(1))''  
  
    # Outputs the Transact SQL to the clipboard and to the screen to create the credential using the Shared Access Signature  
    Write-Host 'Credential T-SQL'  
    $tSql = "CREATE CREDENTIAL [{0}] WITH IDENTITY='Shared Access Signature', SECRET='{1}'" -f $cbc.Uri,$sas.Substring(1)   
    $tSql | clip  
    Write-Host $tSql  
  
    ```  
  
3.  Cuando finalice el script, la instrucción CREATE CREDENTIAL estará en el Portapapeles para poder usarla en la siguiente lección.  
  
**Lección siguiente:**  
  
[Lección 2: Crear una credencial de SQL Server con una firma de acceso compartido](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
## <a name="see-also"></a>Ver también  
[Firmas de acceso compartido, Parte 1: Descripción del modelo SAS](https://azure.microsoft.com/en-us/documentation/articles/storage-dotnet-shared-access-signature-part-1/)  
[Crear contenedor](https://msdn.microsoft.com/library/azure/dd179468.aspx)  
[Establecer lista de control de acceso de contenedor](https://msdn.microsoft.com/library/azure/dd179391.aspx)  
[Obtener lista de control de acceso de contenedor](https://msdn.microsoft.com/library/azure/dd179469.aspx)  
  
  
  

