---
title: Componentes de SQL Server Native Client | Documentos de Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], components
- components [SQL Server Native Client]
- SQLNCLI, about SQL Server Native Client
ms.assetid: 65f932d5-daa1-4eff-b6df-ee633fcf2a7c
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 3cde9f9f212bdb0290b04b61247ad9d37631e815
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39539265"
---
# <a name="components-of-sql-server-native-client"></a>Componentes de SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client contiene los componentes siguientes:  
  
|Componente|Descripción|  
|---------------|-----------------|  
|sqlncli11.dll|El archivo de biblioteca de vínculos dinámicos (DLL) que contiene toda la funcionalidad de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Esto incluye el proveedor OLE DB de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client y el controlador ODBC de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|sqlnclir11.rll|El archivo de recursos adjunto para la biblioteca de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|   
|sqlncli.h|El archivo de encabezado de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client que contiene todas las definiciones nuevas necesarias para utilizar [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Este archivo de encabezado reemplaza a los archivos de encabezado odbcss.h y sqloledb.h.<br /><br /> Nota: No se puede hacer referencia a sqlncli.h y odbcss.h en el mismo programa, pero puede hacer referencia a sqlncli.h y sqloledb.h en el mismo programa como sqloledb.h se define en primer lugar.|  
|sqlncli11.lib|El archivo de biblioteca necesario directamente llamada la **bcp** funciones de utilidad que forman parte de la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] controlador ODBC Native Client.<br /><br /> Nota: Si el archivo sqlncli11.lib hace referencia en el código de programación, debe asegurarse de que el archivo sqlncli11.dll está en la ruta del sistema y en la ruta del sistema de los usuarios que hacen uso de la aplicación.|  
  
## <a name="see-also"></a>Vea también  
 [Generar aplicaciones con SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
