---
title: "LTRIM (expresi&#243;n de SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "espacio en blanco iniciales"
  - "LTRIM, función"
ms.assetid: d082f42a-d7e7-49f5-a503-ac44ba630832
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# LTRIM (expresi&#243;n de SSIS)
  Devuelve una expresión de caracteres tras quitar todos los espacios iniciales en blanco.  
  
> [!NOTE]  
>  LTRIM no quita los caracteres de espacio en blanco, como los caracteres de tabulación o de salto de línea. Unicode proporciona puntos de código para muchos tipos distintos de espacios, pero su función solo reconoce el punto de código Unicode 0x0020. Cuando se convierten cadenas del juego de caracteres de doble byte (DBCS) a Unicode, éstas pueden incluir caracteres de espacio distintos de 0x0020 y la función no puede eliminarlos. Para eliminar cualquier tipo de espacio, puede utilizar el método LTrim de Microsoft Visual Basic .NET en un script ejecutado desde el componente Script.  
  
## Sintaxis  
  
```  
  
LTRIM(character expression)  
```  
  
## Argumentos  
 *character_expression*  
 Expresión de caracteres de la que puede quitar espacios.  
  
## Tipos de resultado  
 DT_WSTR  
  
## Comentarios  
 LTRIM solo funciona con el tipo de datos DT_WSTR. Un argumento *character_expression* que sea un literal de cadena o una columna de datos con el tipo de datos DT_STR se convertirá implícitamente al tipo de datos DT_WSTR antes de que LTRIM realice su operación. Los otros tipos de datos deben convertirse explícitamente al tipo de datos DT_WSTR. Para obtener más información, vea [Tipos de datos de Integration Services](../../integration-services/data-flow/integration-services-data-types.md) y [Conversión &#40;expresión de SSIS&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
 LTRIM devuelve un resultado NULL si el valor del argumento es NULL.  
  
## Ejemplos de expresiones  
 Este ejemplo quita los espacios iniciales de un literal de cadena. El resultado devuelto es "Hello".  
  
```  
LTRIM("    Hello")  
```  
  
 Este ejemplo quita los espacios iniciales de los valores de la columna **FirstName** .  
  
```  
LTRIM(FirstName)  
```  
  
 Este ejemplo quita los espacios iniciales de los valores de la variable **FirstName** .  
  
```  
LTRIM(@FirstName)  
```  
  
## Vea también  
 [RTRIM &#40;expresión de SSIS&#41;](../../integration-services/expressions/rtrim-ssis-expression.md)   
 [TRIM &#40;expresión de SSIS&#41;](../../integration-services/expressions/trim-ssis-expression.md)   
 [Funciones &#40;expresión de SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  