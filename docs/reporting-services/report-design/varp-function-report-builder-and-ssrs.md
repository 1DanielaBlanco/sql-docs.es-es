---
title: "Funci&#243;n VarP (Generador de informes y SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e4f86ab3-bdb3-4e4a-9a9d-7ae7abdf4dc4
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# Funci&#243;n VarP (Generador de informes y SSRS)
  Devuelve la varianza de población de todos los valores numéricos no NULL especificados por la expresión, que se evalúa en el contexto del ámbito especificado.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Sintaxis  
  
```  
  
VarP(expression, scope, recursive)  
```  
  
#### Parámetros  
 *expression*  
 (**Integer** o **Float**) Expresión en la que se realiza la agregación.  
  
 *ámbito*  
 (**String**) Opcional. Nombre de un conjunto de datos, un grupo o una región de datos que contiene los elementos de informe a los que se va a aplicar la función de agregado. Si no se especifica el parámetro *scope* , se usa el ámbito actual.  
  
 *recursivos*  
 (**Enumerated Type**) Opcional. **Simple** (valor predeterminado) o **RdlRecursive**. Especifica si se debe realizar la agregación de forma recursiva.  
  
## Tipo devuelto  
 Devuelve un valor **Decimal** para expresiones decimales y un valor **Double** para las demás expresiones.  
  
## Comentarios  
 El conjunto de datos especificado en la expresión debe tener el mismo tipo de datos. Si desea convertir datos de varios tipos de datos numéricos al mismo tipo de datos, use funciones de conversión como **CInt**, **CDbl** o **CDec**. Para obtener más información, vea [Funciones de conversión de tipos](http://go.microsoft.com/fwlink/?LinkId=96142).  
  
 El valor de *scope* debe ser una constante de cadena y no puede ser una expresión. Para los agregados exteriores o los que no especifican a otros agregados, *scope* debe hacer referencia al ámbito actual o a un ámbito de contenido. Para los agregados de agregados, los agregados anidados pueden especificar un ámbito secundario.  
  
 *Expression* puede contener las llamadas a las funciones de agregados anidados con las siguientes excepciones y condiciones:  
  
-   *Scope* , para los agregados anidados, debe ser igual que el ámbito del agregado exterior, o ser contenido por él. Para todos los ámbitos distintos de la expresión, un ámbito debe estar en una relación secundaria con respecto a todos los otros ámbitos.  
  
-   *Scope* , para los agregados anidados, no puede ser el nombre de un conjunto de datos.  
  
-   *Expression* no debe contener las funciones **First**, **Last**, **Previous**o **RunningValue** .  
  
-   *Expression* no debe contener a los agregados anidados que especifican *recursive*.  
  
 Para más información, vea [Referencia a las funciones de agregado &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md) y [Ámbito de expresión para los totales, agregados y colecciones integradas &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md).  
  
 Para más información sobre los agregados recursivos, vea [Crear grupos de jerarquía recursiva &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## Ejemplo  
 El siguiente ejemplo de código devuelve la varianza de población de los totales para cada artículo del grupo o de la región de datos `Order` .  
  
```  
=VarP(Fields!LineTotal.Value, "Order")  
```  
  
## Vea también  
 [Usar expresiones en informes &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Ejemplos de expresiones &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Tipos de datos en expresiones &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Ámbito de expresión para los totales, agregados y colecciones integradas &#40;Generador de informes y SSRS&#41;](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md)  
  
  