---
title: Datos de flujos de datos | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting data types [Integration Services]
- comparing data
- data types [Integration Services], data flow
- parsing [Integration Services]
- string comparisons
- data flow [Integration Services], data options
ms.assetid: 8a9d6186-eb52-48e3-997e-021f24d458a3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: dcc79e1bcb8e871b5424e9e4995db58e1f97a513
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692878"
---
# <a name="data-in-data-flows"></a>Datos de flujos de datos
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] proporciona un conjunto de tipos de datos que se usan en flujos de datos.  
  
## <a name="data-type-conversion"></a>Conversión de tipo de datos  
 El origen que se agrega a un flujo de datos convierte los datos de origen en tipos de datos de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Las transformaciones posteriores pueden convertir los datos en diferentes tipos de datos de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] y, según el tipo de almacén de datos en el que se cargan los datos, los destinos pueden convertir el tipo de datos final de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en el tipo de datos requerido por el almacén de datos de destino. Para más información, consulte [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Para convertir los datos a un tipo de datos de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , un componente de flujo de datos analiza los datos. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] proporciona dos tipos de análisis de datos: el análisis rápido y el análisis estándar. La mayoría de los componentes de flujo de datos puede usar solamente el análisis estándar. Sin embargo, el origen de archivo plano y la transformación Conversión de datos pueden usar el análisis rápido o estándar. Para más información, consulte [Parsing Data](../../integration-services/data-flow/parsing-data.md).  
  
## <a name="data-type-comparison"></a>Comparación de tipos de datos  
 Muchas transformaciones comparan valores de datos. Por ejemplo, la transformación Agregado compara valores con el fin de agregar valores en un conjunto de filas de datos, la transformación Ordenar compara valores para ordenarlos y la transformación Búsqueda compara valores con valores en una tabla de referencia independiente. Para especificar la forma en que se deben comparar las cadenas, la transformación incluye un conjunto de opciones de comparación, tales como pasar por alto la distinción entre mayúsculas y minúsculas, cómo tratar el tipo de escritura kana en un texto japonés, o si se deben omitir los caracteres de espacios en blanco en la cadena. Para más información, consulte [Comparing String Data](../../integration-services/data-flow/comparing-string-data.md).  
  
 El evaluador de expresiones también compara los valores de datos cuando evalúa las expresiones utilizadas por las variables, restricciones de precedencia y transformaciones.  
  
## <a name="data-flow-troubleshooting"></a>Solucionar problemas de flujo de datos  
 Una vez que ha implementado un paquete en el catálogo de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , puede analizar el flujo de datos en el paquete durante la ejecución para comprobar el rendimiento o buscar si hay algún otro problema. Hay informes estándar disponibles que le permiten ver el estado del paquete y el historial y consultar las vistas de la base de datos que proporcionan información detallada sobre la ejecución del paquete. También puede agregar y quitar dinámicamente las derivaciones de datos durante la ejecución de los componentes específicos de destino del paquete. Para más información, consulte [Debugging Data Flow](../../integration-services/troubleshooting/debugging-data-flow.md).  
  
  
