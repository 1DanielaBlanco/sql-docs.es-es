---
title: Sintaxis de literales de intervalo | Documentos de Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- literals [ODBC], interval
- interval literals [ODBC]
- ODBC literals [ODBC], interval
ms.assetid: 2f2d22c1-51d6-4055-9f5a-53bc31e9fea0
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 34f144b270e1820234503189fd5315da539428bc
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2017
---
# <a name="interval-literal-syntax"></a>Sintaxis de literales de intervalo
La siguiente sintaxis se utiliza para los literales de intervalo en ODBC.  
  
 *literal de intervalo:: = intervalo* [+*&#124;* -] *intervalo-calificador de cadena de intervalo*  
  
 *intervalo de-cadena* :: = *oferta* { *literal de mes del año* &#124; *literal de hora del día* } *comillas*  
  
 *literal de mes del año* :: = *valor del año* &#124; [*valor del año* -] *valor de los meses*  
  
 *literal de hora del día* :: = *intervalo de tiempo del día* &#124; *intervalo de tiempo*  
  
 *intervalo de tiempo del día* :: = *valor días* [*horas valor* [:*valor de los minutos*[:*valor de los segundos*]]]  
  
 *intervalo de tiempo* :: = *horas valor* [:*valor de los minutos* [:*valor de los segundos* ]]  
  
 &#124; *valor de los minutos* [:*valor de los segundos* ]  
  
 &#124; *valor de los segundos*  
  
 *valor del año* :: = *valor de fecha y hora*  
  
 *valor de los meses* :: = *valor de fecha y hora*  
  
 *valor de los días* :: = *valor de fecha y hora*  
  
 *valor de horas* :: = *valor de fecha y hora*  
  
 *valor de los minutos* :: = *valor de fecha y hora*  
  
 *valor de los segundos* :: = *valor del entero de segundos* [. [ *fracción de segundos*]]  
  
 *valor del entero de segundos* :: = *entero sin signo*  
  
 *fracción de segundos* :: = *entero sin signo*  
  
 *valor de fecha y hora* :: = *entero sin signo*  
  
 *calificador de intervalo* :: = *campo iniciar* TO *campo final* &#124; *un solo campo de fecha y hora*  
  
 *campo de inicio* :: = *segundo no-datetime-campo* [(*intervalo inicial campo precisión* )]  
  
 *campo final* :: = *segundo no-datetime-campo* &#124; SEGUNDO [(*intervalo de fracciones de segundos-precisión*)]  
  
 *un solo campo de fecha y hora* :: = *segundo no-datetime-campo* [(*intervalo inicial campo precisión*)] &#124; SEGUNDO [(*intervalo inicial campo precisión* [, (*intervalo de fracciones de segundos-precisión*)]  
  
 *campo de fecha y hora* :: = *segundo no-datetime-campo* &#124; SEGUNDO  
  
 *segundo no-datetime-campo* :: = año &#124; MES &#124; DÍA &#124; HORA &#124; MINUTO  
  
 *intervalo de fracciones de segundos-precisión* :: = *entero sin signo*  
  
 *intervalo inicial campo precisión* :: = *entero sin signo*  
  
 *oferta* :: = '  
  
 *entero sin signo* :: = *dígitos...*
