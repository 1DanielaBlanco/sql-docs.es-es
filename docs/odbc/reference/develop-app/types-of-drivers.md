---
title: Tipos de controladores | Documentos de Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- driver compatibility issues [ODBC]
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
ms.assetid: 864c53c1-b68a-48b6-b6bc-5ecb520bb9dc
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 464ba066af26c84c35f178b1a008d2e10a852119
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="types-of-drivers"></a>Tipos de controladores
Controladores ODBC se pueden clasificar como sigue:  
  
-   **2 de ODBC de 32 bits.**  
     ***x* controlador** controladores de 32 bits que:  
  
    -   Exporta solo ODBC 2*.x* funciones.  
  
    -   Exhibe ODBC 2. *x* comportamiento para cambios de comportamiento.  
  
-   **ISO y abrir el controlador compatible con el grupo** controladores de 32 bits que:  
  
    -   Exporta todas las funciones que se documentan en los documentos de Open Group o ISO CLI. Esto incluye algunas de las funciones que están en desuso en ODBC.  
  
    -   Se comporta de ODBC 3.0 para cambios de comportamiento.  
  
    -   No necesariamente pasa a través del Administrador de controladores ODBC 3.0.  
  
-   **Controladores ODBC 3.0** controladores de 32 bits que:  
  
    -   Las exportaciones solo las funciones que se encuentran en ODBC 3.0 menos funciones en desuso.  
  
    -   Es capaz de cuello de ODBC 2. *x* comportamiento o ODBC 3.0 con respecto a los cambios de comportamiento, según el atributo de entorno SQL_ATTR_APP_ODBC_VERSION.  
  
-   **Controlador ODBC 3.5 (o posterior) ANSI** controladores de 32 bits que:  
  
    -   Las exportaciones solo las funciones que se encuentran en ODBC 3.5 menos funciones en desuso.  
  
    -   Es capaz de cuello de ODBC 2. *x* comportamiento o comportamiento de ODBC 3.0 o comportamiento de ODBC 3.5 con respecto a los cambios de comportamiento, según el atributo de entorno SQL_ATTR_APP_ODBC_VERSION.  
  
-   **Controlador ODBC 3.5 (o posterior) Unicode** controladores de 32 bits que:  
  
    -   Es compatible con todas las características de un controlador de ODBC 3.5 ANSI.  
  
    -   Exporta las versiones de Unicode de todas las API de cadenas ODBC.  
  
    -   Puede almacenar y procesar los datos de Unicode en el origen de datos.  
  
> [!NOTE]  
>  controladores ODBC de 16 bits no funciona directamente con ODBC 3. *x* el Administrador de controladores. Sin embargo, es posible que los controladores de 16 bits trabajar con el Administrador de controladores ODBC 2.0, que posteriormente códigos thunk hasta el 3. *x* el Administrador de controladores.

