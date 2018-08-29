---
title: Propiedades del origen de configuración de los datos | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f3363d05-07fc-4bf8-ae5e-2a7a968808ad
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 000d33df0320333e688051f1888659d152f62dde
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42786176"
---
# <a name="setting-the-data-source-properties"></a>Establecer las propiedades de los orígenes de datos

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Los orígenes de datos son el mecanismo preferido por el que crear conexiones de JDBC en un entorno Java Platform, Enterprise Edition (Java EE). Los orígenes de datos proporcionan conexiones, conexiones agrupadas y conexiones distribuidas sin codificar de forma rígida las propiedades de la conexión en código Java. Todos los orígenes de datos del [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] pueden establecer u obtener el valor de cualquier propiedad mediante los métodos adecuados de establecedor y captador, respectivamente.

Los productos de Java EE, tales como servidores de aplicaciones y motores de servlet/JSP, normalmente le permiten configurar los orígenes de datos para el acceso a bases de datos. Todas las propiedades enumeradas en el tema [Establecer las propiedades de conexión](../../connect/jdbc/setting-the-connection-properties.md) se pueden especificar siempre que la configuración permita escribir una propiedad como un par propiedad=valor.

Para obtener más información sobre los orígenes de datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vea la clase [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md). Para obtener un ejemplo de cómo usar la clase SQLServerDataSource para establecer una conexión con un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de base de datos, vea [muestra del origen de datos](../../connect/jdbc/data-source-sample.md).

## <a name="see-also"></a>Ver también

[Conexión a SQL Server con el controlador JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
