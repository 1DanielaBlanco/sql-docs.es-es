---
title: Compatibilidad entre versiones | Documentos de Microsoft
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
- table-valued parameters (ODBC), cross-version compatibility
ms.assetid: 5f14850b-b85c-41e2-8116-6f5b3f5e0856
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d256fe042562f902aeb3e6229b36f25308e3c138
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36106947"
---
# <a name="cross-version-compatibility"></a>Compatibilidad entre versiones
  Pueden producirse conflictos entre versiones cuando se espera que las instancias cliente o servidor de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anteriores a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] procesen los parámetros con valores de tabla.  
  
 En general, la funcionalidad de los parámetros con valores de tabla solo está disponible para los clientes de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (con SQL Server Native Client 10.0) o posterior que están conectados a los servidores de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (o posterior). Las nuevas columnas en conjuntos de resultados de función de catálogo solo estarán presentes cuando se conecta a un [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (o posterior) server.  
  
 Si una aplicación cliente compilada con una versión anterior de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ejecuta instrucciones que esperan parámetros con valores de tabla, el servidor detecta esta condición a través de un error de conversión de datos y ODBC devuelve esto como SQLSTATE 07006 y el mensaje "Infracción del atributo de tipo de datos restringido".  
  
 Si una aplicación cliente que se compiló con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10.0 o posterior intenta utilizar parámetros con valores de tabla cuando se conecta a una instancia de servidor anterior a [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client detectará esto y SQLBindCol, Llamadas SQLBindParameter, SQLSetDescFields y SQLSetDescRec se producirá un error con SQLSTATE 07006 y el mensaje "Restricted infracción del atributo de tipo de datos (la versión de SQL Server para esta conexión no admite parámetros con valores de tabla)".  
  
## <a name="see-also"></a>Vea también  
 [Parámetros con valores de tabla &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  