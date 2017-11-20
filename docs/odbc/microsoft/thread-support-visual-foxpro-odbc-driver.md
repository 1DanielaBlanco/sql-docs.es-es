---
title: "Subprocesos de soporte técnico (el controlador ODBC de Visual FoxPro) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- thread support [ODBC]
- Visual FoxPro ODBC driver [ODBC], thread support
- FoxPro ODBC driver [ODBC], thread support
- multithreaded applications [ODBC]
ms.assetid: 0c6abbbc-012b-41aa-bded-5e7e362d015b
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cd540c727f1e8a77dbb6d8201715c213ff688909
ms.contentlocale: es-es
ms.lasthandoff: 09/09/2017

---
# <a name="thread-support-visual-foxpro-odbc-driver"></a>Compatibilidad con subprocesos (el controlador ODBC de Visual FoxPro)
El controlador ODBC de Visual FoxPro es segura para subprocesos. Acceso a los identificadores de entorno (*uando*), identificadores de conexión (*hdbc*) y los identificadores de instrucciones (*hstmt*) se ajusta en semáforos adecuados para evitar que otros procesos obtengan acceso y potencialmente modificar estructuras de datos internas del controlador.  
  
 En una aplicación multiproceso, puede cancelar una función que se ejecuta de forma sincrónica en un *hstmt* mediante una llamada a [SQLCancel](../../odbc/microsoft/sqlcancel-visual-foxpro-odbc-driver.md) en un subproceso independiente.  
  
 El controlador usa un subproceso independiente para capturar los datos cuando se usa obtener progresiva. Para utilizar la obtención de progresiva para un origen de datos, seleccione la **capturar los datos en segundo plano** casilla de verificación en la [cuadro de diálogo del programa de instalación de Visual FoxPro ODBC](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md) o usar la palabra clave de atributo de BackgroundFetch en la conexión cadena. Evite utilizar la captura de fondo cuando se invoque el controlador desde aplicaciones multiproceso. Para obtener información sobre las palabras clave de atributo de cadena de conexión, vea [uso de cadenas de conexión](../../odbc/microsoft/using-connection-strings.md).  
  
 Para obtener más información acerca de los subprocesos y **SQLCancel**, consulte [SQLCancel](../../odbc/reference/syntax/sqlcancel-function.md) en el *referencia del programador de ODBC*.

