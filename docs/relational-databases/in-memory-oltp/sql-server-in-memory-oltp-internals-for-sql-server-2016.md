---
title: "Parámetros internos de OLTP en memoria de SQL Server para SQL Server 2016 | Microsoft Docs"
ms.custom: 
ms.date: 09/14/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: in-memory-oltp
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b14da361-a6b8-4d85-b196-7f2f13650f44
caps.latest.revision: "2"
author: jodebrui
ms.author: jodebrui
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3198c31d84cc06c5a559caedd3d0af2c1496bb0d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="sql-server-in-memory-oltp-internals-for-sql-server-2016"></a>Parámetros internos de OLTP en memoria de SQL Server para SQL Server 2016
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**Resumen:** OLTP en memoria, denominada normalmente por su nombre en código "Hekaton", se introdujo en SQL Server 2014.
Esta eficaz tecnología permite sacar partido de grandes cantidades de memoria y varias decenas de núcleos para aumentar el rendimiento de las operaciones OLTP de 30 a 40 veces. SQL Server 2016 continúa la inversión en OLTP en memoria mediante la eliminación de muchas de las limitaciones que se encuentran en SQL Server 2014 y la mejora de los algoritmos de procesamiento interno para que OLTP en memoria pueda proporcionar mejoras todavía mayores. En este documento se describe la implementación de tecnología OLTP en memoria de SQL Server 2016 a partir de SQL Server 2016 RTM. Al usar OLTP en memoria, las tablas se pueden declarar como "optimizada en memoria" para habilitar las capacidades de OLTP en memoria. Las tablas optimizadas en memoria son completamente transaccionales y se puede acceder a ellas mediante Transact-SQL. Los procedimientos almacenados de Transact-SQL, los desencadenadores y los UDF escalares se pueden compilar en código de máquina para obtener nuevas mejoras de rendimiento en tablas optimizadas en memoria. El motor está diseñado para obtener una alta simultaneidad sin ningún bloqueo.    
  
**Escritor:** Kalen Delaney  
  
**Revisores técnicos:** Sunil Agarwal y Jos de Bruijn  
  
**Publicado:** junio de 2016  
  
**Se aplica a:** SQL Server 2016  
  
Para revisar el documento, descargue el documento [Parámetros internos de OLTP en memoria de SQL Server para SQL Server 2016](http://download.microsoft.com/download/8/3/6/8360731A-A27C-4684-BC88-FC7B5849A133/SQL_Server_2016_In_Memory_OLTP_White_Paper.pdf) .   
