---
title: Especificar un eje (SQLXML 4.0) | Documentos de Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], axes
- XPath queries [SQLXML], location paths
- self axis
- attribute axis [SQLXML]
- axis [SQLXML]
- child axis
- parent axis
- location path for XPath query
- axes [SQLXML]
ms.assetid: 65631795-3389-40cf-90ea-85e9438956c5
caps.latest.revision: "22"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 40deac488a6a5d793689668e3acc5f0971bb3a61
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="specifying-an-axis-sqlxml-40"></a>Especificar un eje (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
    
-   El eje especifica la relación jerárquica entre los nodos seleccionados por el paso de ubicación y el nodo de contexto. Se admiten los ejes siguientes: **secundarios**  
  
     Contiene el elemento secundario del nodo de contexto.  
  
     La expresión XPath siguiente (ruta de acceso de ubicación) selecciona del nodo de contexto actual todos los  **\<cliente >** elementos secundarios:  
  
    ```  
    child::Customer  
    ```  
  
     En la consulta XPath siguiente, `child` es el eje. `Customer` es la prueba de nodo.  
  
-   **elemento primario**  
  
     Contiene el elemento primario del nodo de contexto.  
  
     La expresión XPath siguiente selecciona todas la  **\<cliente >** elementos primarios de la  **\<orden >** elementos secundarios:  
  
    ```  
    child::Customer/child::Order[parent::Customer/@customerID="ALFKI"]  
    ```  
  
     Esto equivale a especificar `child::Customer`. En esta consulta XPath, `child` y `parent` son los ejes. `Customer` y `Order` son las pruebas de nodo.  
  
-   **atributo**  
  
     Contiene el atributo del nodo de contexto.  
  
     La expresión XPath siguiente selecciona el **CustomerID** atributo del nodo de contexto:  
  
    ```  
    attribute::CustomerID  
    ```  
  
-   **en sí mismo**  
  
     Contiene el propio nodo de contexto.  
  
     La expresión XPath siguiente selecciona el nodo actual si es el  **\<orden >** nodo:  
  
    ```  
    self::Order  
    ```  
  
     En esta consulta XPath, `self` es el eje y `Order` es la prueba de nodo.  
  
  
