---
title: BEGIN DISTRIBUTED TRANSACTION (Transact-SQL) | Documentos de Microsoft
ms.custom: 
ms.date: 11/29/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DISTRIBUTED
- BEGIN_DISTRIBUTED_TRANSACTION_TSQL
- DISTRIBUTED_TSQL
- BEGIN DISTRIBUTED TRANSACTION
dev_langs:
- TSQL
helpviewer_keywords:
- BEGIN DISTRIBUTED TRANSACTION statement
- distributed transactions [SQL Server], starting
- MS DTC, transaction management
- distributed transactions [SQL Server], BEGIN DISTRIBUTED TRANSACTION statement
- servers [SQL Server], distributed transactions
- starting distributed transactions
- remote servers [SQL Server], distributed transactions
- starting transactions
ms.assetid: c3bc2716-39d3-4061-8c6a-8734899231ac
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 93287230933c8ad33bc72185b2b26402ef8048fa
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="begin-distributed-transaction-transact-sql"></a>BEGIN DISTRIBUTED TRANSACTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Especifica el inicio de una transacción distribuida de [!INCLUDE[tsql](../../includes/tsql-md.md)] administrada mediante el Coordinador de transacciones distribuidas de [!INCLUDE[msCoName](../../includes/msconame-md.md)] (MS DTC).  
    
  
 ![Icono de vínculo de tema](../../database-engine/configure-windows/media/topic-link.gif "Icono de vínculo de tema") [Convenciones de sintaxis de Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
BEGIN DISTRIBUTED { TRAN | TRANSACTION }   
     [ transaction_name | @tran_name_variable ]   
[ ; ]  
```  
  
## <a name="arguments"></a>Argumentos  
 *transaction_name*  
 Se trata de un nombre de transacción definida por el usuario que se utiliza para realizar el seguimiento de la transacción distribuida en las utilidades de MS DTC. *transaction_name* debe cumplir las reglas para identificadores y debe ser \<= 32 caracteres.  
  
 @*tran_name_variable*  
 Se trata del nombre de una variable definida por el usuario que contiene el nombre de una transacción utilizada para realizar el seguimiento de la transacción distribuida en las utilidades de MS DTC. La variable debe declararse con una **char**, **varchar**, **nchar**, o **nvarchar** tipo de datos.  
  
## <a name="remarks"></a>Comentarios  
 La instancia del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] que ejecuta la instrucción BEGIN DISTRIBUTED TRANSACTION es el originador de la transacción y controla su realización. Posteriormente, cuando en la sesión se ejecuta una instrucción COMMIT TRANSACTION o ROLLBACK TRANSACTION, la instancia que controla la transacción solicita a MS DTC que administre la realización de la transacción distribuida entre todas las instancias participantes.  
  
 El aislamiento de instantáneas de nivel de instantánea no admite transacciones distribuidas.  
  
 La principal manera en que las instancias remotas del [!INCLUDE[ssDE](../../includes/ssde-md.md)] se dan de alta en una transacción distribuida es cuando una sesión ya dada de alta en la transacción distribuida ejecuta una consulta distribuida que hace referencia a un servidor vinculado.  
  
 Por ejemplo, si BEGIN DISTRIBUTED TRANSACTION se ejecuta en ServerA, la sesión llama a un procedimiento almacenado en ServerB y a otro procedimiento almacenado en ServerC. El procedimiento almacenado en ServerC ejecuta una consulta distribuida en ServerD y, a continuación, los cuatro equipos participan en la transacción distribuida. La instancia del [!INCLUDE[ssDE](../../includes/ssde-md.md)] en ServerA es la instancia de origen que controla la transacción.  
  
 Las sesiones que participan en transacciones distribuidas de [!INCLUDE[tsql](../../includes/tsql-md.md)] no obtienen un objeto de transacción que puedan pasar a otra sesión para que se dé de alta explícitamente en la transacción distribuida. La única forma en que un servidor remoto puede darse de alta en la transacción consiste en que constituya el destino de una llamada a un procedimiento almacenado remoto o a una consulta distribuida.  
  
 Cuando se ejecuta una consulta distribuida en una transacción local, la transacción se promueve automáticamente a una transacción distribuida si el origen de datos de OLE DB de destino es compatible con ITransactionLocal. Si el origen de datos de OLE DB de destino no es compatible con ITransactionLocal, solo las operaciones de solo lectura se permiten en la consulta distribuida.  
  
 Una sesión que ya se ha dado de alta en la transacción distribuida realiza una llamada a un procedimiento almacenado remoto que hace referencia a un servidor remoto.  
  
 El **transacciones de procedimientos remotos sp_configure** opción controla si las llamadas a procedimientos almacenados remotos en una transacción local provocan automáticamente que la transacción local se promueva a una transacción distribuida administrada mediante MS DTC. La opción SET de nivel de conexión REMOTE_PROC_TRANSACTIONS puede utilizarse para invalidar el valor de instancia predeterminado establecido por **transacciones de procedimientos remotos sp_configure**. Con esta opción activada, la llamada a un procedimiento almacenado remoto hace que una transacción local se promueva al nivel de transacción distribuida. La conexión que crea la transacción de MS DTC se convierte en el originador de la transacción. COMMIT TRANSACTION inicia una confirmación coordinada de MS DTC. Si el **transacciones de procedimientos remotos sp_configure** opción está activada, llamadas a procedimientos almacenados remotos en transacciones locales se protegen automáticamente como parte de transacciones distribuidas sin tener que volver a escribir las aplicaciones específicamente problema BEGIN DISTRIBUTED TRANSACTION en lugar de BEGIN TRANSACTION.  
  
 Para obtener más información sobre el entorno y el proceso de transacciones distribuidas, vea la documentación del Coordinador de transacciones distribuidas de [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
## <a name="permissions"></a>Permissions  
 Debe pertenecer al rol public.  
  
## <a name="examples"></a>Ejemplos  
 Este ejemplo elimina un candidato de la base de datos [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] tanto en la instancia local del [!INCLUDE[ssDE](../../includes/ssde-md.md)] como en la instancia de un servidor remoto. Ambas bases de datos, local y remota, confirmarán o revertirán la transacción.  
  
> [!NOTE]  
>  A menos que MS DTC esté instalado actualmente en el equipo que ejecuta la instancia del [!INCLUDE[ssDE](../../includes/ssde-md.md)], este ejemplo produce un mensaje de error. Para obtener más información sobre cómo instalar Microsoft DTC, vea la documentación de Microsoft DTC (Coordinador de transacciones distribuidas).  
  
```  
USE AdventureWorks2012;  
GO  
BEGIN DISTRIBUTED TRANSACTION;  
-- Delete candidate from local instance.  
DELETE AdventureWorks2012.HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
-- Delete candidate from remote instance.  
DELETE RemoteServer.AdventureWorks2012.HumanResources.JobCandidate  
    WHERE JobCandidateID = 13;  
COMMIT TRANSACTION;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [BEGIN TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-transaction-transact-sql.md)   
 [COMMIT TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/commit-transaction-transact-sql.md)   
 [TRABAJO de confirmación &#40; Transact-SQL &#41;](../../t-sql/language-elements/commit-work-transact-sql.md)   
 [ROLLBACK TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/rollback-transaction-transact-sql.md)   
 [ROLLBACK WORK &#40; Transact-SQL &#41;](../../t-sql/language-elements/rollback-work-transact-sql.md)   
 [SAVE TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/save-transaction-transact-sql.md)  
  
  

