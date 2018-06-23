---
title: Extensiones específicas en proceso SQL Server a ADO.NET | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [CLR integration]
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- database objects [CLR integration], in-process extensions
- in-process data access providers [CLR integration]
- extensions [CLR integration]
ms.assetid: 781b812e-eb14-472a-85fa-aa4cdb929bee
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b72ecf75f7c696e21fc14e73b42d1d192320679e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36108612"
---
# <a name="sql-server-in-process-specific-extensions-to-adonet"></a>Extensiones específicas en proceso de SQL Server a ADO.NET
  Hay cuatro extensiones funcionales principales a ADO.NET que son específicamente para el uso en proceso. En los siguientes temas se tratan estas extensiones en detalle.  
  
## <a name="in-this-section"></a>En esta sección  
 [Objeto SqlContext](sqlcontext-object.md)  
 Esta clase proporciona acceso a las demás extensiones abstrayendo el contexto de llamador de una rutina de SQL Server que ejecuta el código administrado en proceso.  
  
 [Objeto SqlPipe](sqlpipe-object.md)  
 Esta clase contiene rutinas para enviar resultados tabulares y mensajes al cliente.  
  
 [Objeto SqlTriggerContext](sqltriggercontext-object.md)  
 Esta clase proporciona información sobre el contexto en el que se ejecuta un desencadenador.  
  
 [Objeto SqlDataRecord](sqldatarecord-object.md)  
 La clase SqlDataRecord representa una única fila de datos, junto con sus metadatos relacionados, y permite que los procedimientos almacenados devuelvan al cliente conjuntos de resultados personalizados.  
  
  