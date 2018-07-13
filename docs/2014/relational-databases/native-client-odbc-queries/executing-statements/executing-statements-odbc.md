---
title: Ejecución de instrucciones (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b50d6e9cc46e9abdf46e2b3b0a184654d9074b8f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37410774"
---
# <a name="executing-statements-odbc"></a>Ejecutar instrucciones (ODBC)
  El [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] controlador ODBC de Native Client ofrece varios modos para ejecutar instrucciones SQL en un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] base de datos:  
  
-   Ejecución directa  
  
-   Ejecución preparada  
  
 Ejecución directa implica la creación de una cadena de caracteres que contiene un [!INCLUDE[tsql](../../../includes/tsql-md.md)] instrucción y enviarlo para su ejecución mediante el **SQLExecDirect** función. La ejecución preparada implica la creación de una cadena de caracteres que contiene una instrucción [!INCLUDE[tsql](../../../includes/tsql-md.md)] y su posterior ejecución en dos fases. La primera fase se utiliza el [SQLPrepare Function](http://go.microsoft.com/fwlink/?LinkId=59360) función para analizar y compilar el plan de ejecución de la instrucción en el [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. La segunda fase se utiliza el **SQLExecute** función para ejecutar el plan de ejecución previamente preparado. De esta forma, se guarda la sobrecarga de análisis y compilación en cada ejecución. Las aplicaciones suelen usar la ejecución preparada para ejecutar repetidamente una misma instrucción SQL parametrizada.  
  
 Tanto en la ejecución directa como en la ejecución preparada puede ejecutarse una única instrucción de [!INCLUDE[tsql](../../../includes/tsql-md.md)] o un lote de instrucciones de SQL, o puede llamarse a un procedimiento almacenado.  
  
## <a name="in-this-section"></a>En esta sección  
  
-   [Ejecución directa](direct-execution.md)  
  
-   [Ejecución preparada](prepared-execution.md)  
  
-   [Procedimientos](procedures.md)  
  
-   [Lotes de instrucciones](batches-of-statements.md)  
  
-   [Efectos de las opciones ISO](effects-of-iso-options.md)  
  
## <a name="see-also"></a>Vea también  
 [Ejecución de consultas &#40;ODBC&#41;](../executing-queries-odbc.md)  
  
  
