---
title: Realizar transacciones en ADOMD.NET | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- transactions [ADOMD.NET]
- ADOMD.NET, transactions
- AdomdTransaction object
ms.assetid: 7978c28b-c255-43c0-ad05-f38604d4d8fe
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2b37257b647dc9c1675e36c0f0b6a9b06bbf08d8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36202193"
---
# <a name="performing-transactions-in-adomdnet"></a>Realizar transacciones en ADOMD.NET
  En ADOMD.NET, usa el objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> para administrar el contexto de transacción para un objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> determinado. Esta funcionalidad le permite ejecutar varios comandos dentro del mismo contexto. Cada comando leerá los mismos datos sin los datos de la lectura que cambian entre cada ejecución de comandos.  
  
> [!NOTE]  
>  La clase <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> es la implementación de la interfaz `System.Data.IDbTransaction`, parte de la biblioteca de clases de [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework e implementada por todos los proveedores de datos de .NET Framework que admiten transacciones.  
  
 El objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> únicamente admite transacciones de lectura confirmada, que contiene los bloqueos compartidos mientras los datos se leen para evitar las lecturas no actualizadas.  
  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> se usa para iniciar la transacción. Para usar la transacción, los comandos se ejecutan en la conexión que inició la transacción. Cuando termine la transacción, puede revertir o confirmar la transacción.  
  
## <a name="starting-a-transaction"></a>Iniciar una transacción  
 Puede crear una instancia de un objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> llamando al método <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.BeginTransaction%2A> del objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>. En el ejemplo siguiente se muestra cómo se crea una instancia del objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction>.  
  
```  
Dim objTransaction As AdomdTransaction = objConnection.BeginTransaction()  
AdomdTransaction objTransaction = objConnection.BeginTransaction();  
```  
  
## <a name="rolling-back-a-transaction"></a>Revertir una transacción  
 Para revertir una transacción existente e incompleta, debe llamar al método <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction.Rollback%2A> del objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction>. Si se llama a este método en una transacción existente y completa, se produce una excepción.  
  
## <a name="committing-a-transaction"></a>Confirmar una transacción  
 Después de llamar al método <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.BeginTransaction%2A> para iniciar una transacción, puede completar la transacción llamando al método <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction.Commit%2A> del objeto <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction>. Si llama a este método en una transacción existente y completa, se produce una excepción.  
  
## <a name="see-also"></a>Vea también  
 [Para establecer conexiones en ADOMD.NET](connections-in-adomd-net.md)   
 [Programación del cliente de ADOMD.NET](adomd-net-client-programming.md)  
  
  