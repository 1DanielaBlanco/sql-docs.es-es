---
title: Generar subcubos en MDX (MDX) | Documentos de Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [MDX], subcubes
- subcubes [MDX]
- filtered views [MDX]
- MDX [Analysis Services], subcubes
- Multidimensional Expressions [Analysis Services], subcubes
- CREATE SUBCUBE statement
ms.assetid: 5403a62b-99ac-4d83-b02a-89bf78bf0f46
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3572204ca3619b2a7e545bdd4bca8c1717ea41c3
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2018
---
# <a name="building-subcubes-in-mdx-mdx"></a>Generar subcubos en MDX (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Un subcubo es un subconjunto de un cubo en la representación de una vista filtrada de los datos subyacentes. El hecho de limitar un cubo a un subcubo permite mejorar el rendimiento de las consultas.  
  
 Para definir un subcubo se puede utilizar la instrucción [CREATE SUBCUBE](../../../mdx/mdx-data-definition-create-subcube.md) , tal como se describe en este tema.  
  
## <a name="create-subcube-syntax"></a>Sintaxis de CREATE SUBCUBE  
 Utilice la siguiente sintaxis para crear un subcubo:  
  
```  
CREATE SUBCUBE Subcube_Identifier AS Subcube_Expression  
```  
  
 La sintaxis de CREATE SUBCUBE es relativamente sencilla. El parámetro *Subcube_Identifier* identifica el cubo en el que se basará el subcubo. El parámetro *Subcube_Expression* selecciona la parte del cubo que se convertirá en el subcubo.  
  
 Una vez creado el subcubo, éste se convierte en el contexto de todas las consultas MDX hasta que termine la sesión o hasta que se ejecute la instrucción [DROP SUBCUBE](../../../mdx/mdx-data-definition-drop-subcube.md) .  
  
### <a name="what-a-subcube-contains"></a>Contenido de un subcubo  
 Aunque la instrucción CREATE SUBCUBE resulte fácil de usar, la instrucción en sí no muestra explícitamente todos los miembros que pasarán a formar parte de un subcubo. La definición de los subcubos se rige por las siguientes reglas:  
  
-   Si se incluye el miembro **(Todos)** de una jerarquía, se deben incluir todos los miembros de la misma.  
  
-   Cuando se incluye un miembro se deben incluir todos sus antecesores y descendientes.  
  
-   Si se incluyen todos los miembros de un nivel, se deben incluir todos los miembros de la jerarquía. Los miembros de otras jerarquías quedan excluidos cuando no existen con miembros del nivel (por ejemplo, una jerarquía desequilibrada como puede ser una ciudad que no incluya clientes).  
  
-   Un subcubo siempre contiene todos los miembros **(Todos)** del cubo.  
  
 Otra característica es el cálculo visual del total de los valores agregados del subcubo. Por ejemplo, imaginemos un subcubo que incluya `USA`, `WA`y `OR`. El valor agregado de `USA` será la suma de `{WA,OR}` puesto que `WA` y `OR` son los únicos estados definidos por el subcubo. El resto de los estados se ignoran.  
  
 Las referencias explícitas a las celdas externas al subcubo devuelven valores de celda cuya evaluación se efectúa en el contexto del cubo completo. Por ejemplo, imagine un subcubo limitado al año en curso. Utiliza la función [ParallelPeriod](../../../mdx/parallelperiod-mdx.md) para comparar el año actual con el anterior. El resultado será la diferencia de los valores, incluso si el valor del año anterior no pertenece al subcubo.  
  
 Por último, si no se sobrescribe el contexto original, las funciones de conjuntos evaluadas en una subselección se evalúan en el contexto de dicha subselección. En caso de que se sobrescriba el contexto, las funciones de conjunto se evalúan en el contexto del cubo completo.  
  
## <a name="create-subcube-example"></a>Ejemplo de CREATE SUBCUBE  
 En el siguiente ejemplo se crea un subcubo que restringe el cubo Budget a las cuentas 4200 y 4300:  
  
 `CREATE SUBCUBE Budget AS SELECT {[Account].[Account].&[4200], [Account].[Account].&[4300] } ON 0 FROM Budget`  
  
 Al haber creado un subcubo para la sesión, las consultas que se realicen a partir de ahora se efectuarán en el subcubo, no en el cubo completo. Por ejemplo, ejecute la siguiente consulta. La consulta solo devolverá los miembros de las cuentas 4200 y 4300.  
  
 `SELECT [Account].[Account].Members ON 0, Measures.Members ON 1 FROM Budget`  
  
## <a name="see-also"></a>Vea también  
 [Establecer el contexto de cubo en una consulta &#40; MDX &#41;](../../../analysis-services/multidimensional-models/mdx/establishing-cube-context-in-a-query-mdx.md)   
 [Aspectos básicos de consulta MDX &#40; Analysis Services &#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
