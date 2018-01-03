---
title: "Tamaño de la columna VARCHAR (controlador ODBC para Oracle) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], ODBC driver for Oracle
- varchar column size [ODBC]
- ODBC driver for Oracle [ODBC], data types
ms.assetid: eb4cb410-3d00-4251-8c5e-a06f36c4dac7
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6002a906b2796cbc2f9f50519c11e846455b3ce9
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="varchar-column-size-odbc-driver-for-oracle"></a>Tamaño de la columna VARCHAR (controlador ODBC para Oracle)
> [!IMPORTANT]  
>  Esta característica se quitará en una versión futura de Windows. Evite utilizar esta característica en nuevos trabajos de desarrollo y tenga previsto modificar las aplicaciones que actualmente la utilizan. En su lugar, utilice el controlador ODBC proporcionado por Oracle.  
  
 En Oracle8, ha aumentado el tamaño máximo de una columna VARCHAR de 2000 a 4.000 bytes. El software de cliente de Oracle 7.3.x no tiene ninguna manera de enlazar un valor de parámetro más de 2000 bytes. Por lo tanto, si crea una tabla con una columna VARCHAR de más de 2000 bytes, no se podrá realizar inserciones con parámetros, las actualizaciones, eliminaciones y las consultas en él con datos que supera el límite de 2000 bytes del software cliente. Dado que tanto el controlador ODBC para Oracle y el proveedor OLE DB para Oracle utilizan consultas, actualizaciones, eliminaciones e inserciones con parámetros, va a notificar errores ORA-01026 en este caso. Datos que esté dentro de los límites que se aplican mediante el software de cliente de Oracle funcionará. Para evitar este límite de 2000 bytes, debe actualizar el software de cliente a Oracle8 (8.0.4.1.1c o superior).
