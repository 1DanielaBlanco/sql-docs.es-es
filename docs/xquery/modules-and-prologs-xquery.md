---
title: "Módulos y prólogos (XQuery) | Documentos de Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- XQuery, prolog
- prolog
ms.assetid: 0f17b4a4-6234-41d4-a996-6db4e27bff7e
caps.latest.revision: "13"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f424809019ad7de0c27b91d4c43563256697c90c
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2017
---
# <a name="modules-and-prologs-xquery"></a>Módulos y prólogos (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [Prólogo de XQuery](../xquery/modules-and-prologs-xquery-prolog.md) es una serie de declaraciones de espacio de nombres. Al utilizar la declaración de espacio de nombres en el prólogo, se puede especificar un enlace entre el prefijo y el espacio de nombres y utilizar el prefijo en el cuerpo de la consulta.  
  
## <a name="implementation-limitations"></a>Limitaciones de la implementación  
 En esta implementación no se admiten las siguientes especificaciones de XQuery:  
  
-   Declaración de módulos (`version`)  
  
-   Declaración de módulos (`module namespace`)  
  
-   Xmpspacedeclaration (`xmlspace`)  
  
-   Declaración de intercalaciones predeterminadas (`declare default collation`)  
  
-   Declaración de identificadores URI base (`declare base-uri`)  
  
-   Declaración de construcciones (`declare construction`)  
  
-   Declaración del orden predeterminado (`declare ordering`)  
  
-   Importación de esquemas (`import schema namespace`)  
  
-   Importación de módulos (`import module`)  
  
-   Declaración de variables en el prólogo (`declare variable`)  
  
-   Declaración de funciones (`declare function`)  
  
## <a name="in-this-section"></a>En esta sección  
 [Prólogo de XQuery](../xquery/modules-and-prologs-xquery-prolog.md)  
 Describe el prólogo de XQuery.  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje XQuery &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)  
  
  
