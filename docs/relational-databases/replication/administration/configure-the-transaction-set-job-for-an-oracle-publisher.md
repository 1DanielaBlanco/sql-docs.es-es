---
title: "Configuración del trabajo del conjunto de transacciones para un publicador de Oracle | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- sp_publisherproperty
- Oracle publishing [SQL Server replication], configuring
ms.assetid: beea1a5c-0053-4971-a68f-0da53063fcbb
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bc2465b338c0fe1d70c901e40b8dd64d338e3e58
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="configure-the-transaction-set-job-for-an-oracle-publisher"></a>Configuración del trabajo del conjunto de transacciones para un publicador de Oracle
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  El trabajo **Xactset** es un trabajo de base de datos de Oracle creado por replicación que se ejecuta en un publicador de Oracle para crear conjuntos de transacciones cuando el agente de registro del LOG no está conectado al publicador. Puede habilitar y configurar este trabajo desde el distribuidor mediante programación con procedimientos almacenados de replicación. Para obtener más información, consulte [Optimizar el rendimiento de publicadores de Oracle](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md).  
  
### <a name="to-enable-the-transaction-set-job"></a>Para habilitar el trabajo del conjunto de transacciones  
  
1.  En el publicador de Oracle, establezca el parámetro de inicialización **job_queue_processes** en un valor suficiente para permitir la ejecución del trabajo Xactset. Para obtener más información acerca de este parámetro, vea la documentación de la base de datos del publicador de Oracle.  
  
2.  En el distribuidor, ejecute [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Especifique el nombre del publicador de Oracle en **@publisher**, un valor **xactsetbatching** en **@propertyname**y un valor **enabled** en **@propertyvalue**.  
  
3.  En el distribuidor, ejecute [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Especifique el nombre del publicador de Oracle en **@publisher**, un valor **xactsetjobinterval** en **@propertyname**y el intervalo del trabajo, en minutos, en **@propertyvalue**.  
  
4.  En el distribuidor, ejecute [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Especifique el nombre del publicador de Oracle en **@publisher**, un valor **xactsetjob** en **@propertyname**y un valor **enabled** en **@propertyvalue**.  
  
### <a name="to-configure-the-transaction-set-job"></a>Para configurar el trabajo del conjunto de transacciones  
  
1.  (Opcional) En el distribuidor, ejecute [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Especifique el nombre del publicador de Oracle en **@publisher**. De esta forma se devuelven las propiedades del trabajo **Xactset** al publicador.  
  
2.  En el distribuidor, ejecute [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Especifique el nombre del publicador de Oracle en **@publisher**, el nombre de la propiedad del trabajo Xactset que se establece en **@propertyname**y la nueva configuración en **@propertyvalue**.  
  
3.  (Opcional) Repita el paso 2 para cada propiedad del trabajo Xactset que se establece. Al cambiar la propiedad **xactsetjobinterval** , debe reiniciar el trabajo en el publicador de Oracle para que se aplique el nuevo intervalo.  
  
### <a name="to-view-properties-of-the-transaction-set-job"></a>Para ver las propiedades del trabajo del conjunto de transacciones  
  
1.  En el distribuidor, ejecute [sp_helpxactsetjob](../../../relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql.md). Especifique el nombre del publicador de Oracle en **@publisher**.  
  
### <a name="to-disable-the-transaction-set-job"></a>Para deshabilitar el trabajo del conjunto de transacciones  
  
1.  En el distribuidor, ejecute [sp_publisherproperty &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Especifique el nombre del publicador de Oracle en **@publisher**, un valor **xactsetjob** en **@propertyname**y un valor **disabled** en **@propertyvalue**.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente habilita el trabajo `Xactset` y establece un intervalo de tres minutos entre ejecuciones.  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../relational-databases/replication/codesnippet/tsql/configure-the-transactio_1.sql)]  
  
## <a name="see-also"></a>Ver también  
 [Optimizar el rendimiento de publicadores de Oracle](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)   
 [Replication System Stored Procedures Concepts](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  
