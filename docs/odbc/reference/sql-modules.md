---
title: Los módulos SQL | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL modules [ODBC]
- sending SQL statements to DBMS [ODBC]
- SQL [ODBC], modules
- modules [ODBC]
- SQL statements [ODBC], modules
ms.assetid: 07551472-87ee-4765-951f-1364ed32f0c0
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10957c8e4a847f13d2dbf4b427382e65ea404c1f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="sql-modules"></a>Módulos SQL
La segunda técnica para enviar instrucciones SQL en el DBMS es a través de módulos. En pocas palabras, un módulo consta de un grupo de procedimientos, que se llaman desde el host de lenguaje de programación. Cada procedimiento contiene una sola instrucción SQL y datos se pasan hacia y desde el procedimiento a través de parámetros.  
  
 Un módulo puede considerarse como una biblioteca de objetos que se vincula al código de aplicación. Sin embargo, exactamente cómo los procedimientos y el resto de la aplicación se vinculan es depende de la implementación. Por ejemplo, los procedimientos pudieron compilados en el código de objeto o vinculados directamente en el código de aplicación, podría ser compilados y almacenados en el DBMS y las llamadas a tener acceso a identificadores de plan que se colocan en el código de aplicación, o podría interpretarse en tiempo de ejecución.  
  
 La ventaja principal de los módulos es que limpiamente independientes instrucciones SQL a partir del lenguaje de programación. En teoría, debe ser posible cambiar una aplicación sin cambiar el otro y basta con volver a vincular.
