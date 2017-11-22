---
title: "CREAR KPI (instrucción, MDX) | Documentos de Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE KPI
- KPI
- CREATE_KPI
- CREATE
helpviewer_keywords:
- CREATE KPI statement
- key performance indicators [MDX]
ms.assetid: 87618fef-95e5-4dd0-a650-aeb60ccbddcb
caps.latest.revision: "18"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 9e153bf489ab3d06eb55c4226677c4913498b9f7
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="mdx-data-definition---create-kpi"></a>Definición de datos MDX - crear KPI
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea un indicador clave de rendimiento (KPI). Un KPI es un conjunto de cálculos asociados a un grupo de medida de un cubo, que se utilizan para evaluar el éxito de una empresa o escenario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
CREATE KPI CURRENTCUBE | <Cube Name>.KPI_Name AS KPI_Value  
   [,Property_Name = Property_Value, ...n]  
```  
  
## <a name="arguments"></a>Argumentos  
 *Nombre_kpi*  
 Cadena válida que proporciona un nombre de KPI.  
  
 *KPI_Value*  
 Una expresión MDX (Expresiones multidimensionales) válida que devuelve un valor numérico.  
  
 *Property_name*  
 Cadena válida que proporciona el nombre de una propiedad de KPI.  
  
 *Property_Value*  
 Expresión escalar válida que define el valor de la propiedad de KPI.  
  
## <a name="remarks"></a>Comentarios  
 Si especifica un cubo distinto del que está conectado actualmente, se genera un error. Por lo tanto, debe utilizar CURRENTCUBE en lugar de un nombre de cubo para indicar el cubo actual.  
  
## <a name="kpi-properties"></a>Propiedades de KPI   
 En la tabla siguiente se enumeran todas las propiedades de KPI. Ninguna de estas propiedades tiene un valor predeterminado. Por consiguiente, hasta que se haya asignado un valor concreto a una propiedad de KPI, las consultas de las propiedades devolverán un valor nulo.  
  
|Identificador de la propiedad|Significado|  
|-------------------------|-------------|  
|GOAL|Expresión MDX válida que devuelve un valor numérico.|  
|STATUS|Expresión MDX válida que devuelve un valor numérico.|  
|STATUS_GRAPHIC|Cadena que define un conjunto de imágenes gráficas que serán utilizadas por la aplicación cliente.|  
|TREND|Expresión MDX válida que devuelve un valor numérico.|  
|TREND_GRAPHIC|Cadena que define un conjunto de imágenes gráficas que serán utilizadas por la aplicación cliente.|  
|WEIGHT|Expresión MDX válida que devuelve un valor numérico.|  
|CURRENT_TIME_MEMBER|Expresión MDX válida que devuelve un miembro de la dimensión Time. CURRENT_TIME_MEMBER establece el punto de referencia para todas las funciones relativas a tiempo.|  
|PARENT_KPI|Cadena que especifica el nombre del KPI primario.|  
|CAPTION|Cadena que la aplicación cliente utiliza como título para el KPI.|  
|DISPLAY_FOLDER|Cadena que especifica la ruta de acceso a la carpeta donde la aplicación cliente mostrará el KPI. La aplicación cliente define el separador de niveles de carpetas. Para las herramientas y clientes proporcionados por [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], la barra diagonal inversa (\\) es el separador de niveles. Para proporcionar varias carpetas para mostrar de un miembro definido, utilice un punto y coma (;) para separar las carpetas|  
|ASSOCIATED_MEASURE_GROUP|Cadena que especifica el nombre del grupo de medida al que deberían remitirse todos los cálculos MDX.|  
  
 Los valores para las propiedades GOAL, STATUS y TREND son expresiones MDX que se deberían evaluar entre -1 y 1. Sin embargo, es la aplicación cliente la que define el intervalo de valores real para estas propiedades. Cuando usa las herramientas y clientes proporcionados por [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] para examinar los KPI, los valores menores que -1 se tratan como -1 y los valores mayores que 1 se tratan como 1.  
  
 STATUS_GRAPHIC y TREND_GRAPHIC son valores de cadena que utiliza la aplicación cliente para identificar el conjunto de imágenes que se ha de mostrar. Estas cadenas definen también el comportamiento de la función de visualización. Este comportamiento incluye el número de estados que se pueden mostrar (normalmente, éste es un número impar) y qué imágenes se han de utilizar para cada uno de esos estados.  
  
### <a name="kpi-graphics-in-sql-server-data-tools"></a>Gráficos KPI en Herramientas de datos de SQL Server  
 En [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], los gráficos KPI pueden tener tres o cinco estados. En la tabla siguiente define los valores para cada uno de esos Estados.  
  
|Número de estados para el gráfico de KPI |Valor de esos estados|  
|--------------------------------------|---------------------------|  
|3|Malo = De -1 a -0,5<br /><br /> Suficiente = De 0,4999 a 0,4999<br /><br /> Bueno = De 0,50 a 1|  
|5|Malo = De -1 a -0,75<br /><br /> Riesgo = De -0,7499 a -0,25<br /><br /> Suficiente = De -0,2499 a 0,2499<br /><br /> En progreso = De 0,25 a -0,7499<br /><br /> Bueno = De 0,75 a 1|  
  
> [!NOTE]  
>  Para algunos gráficos, como la medida invertida o la flecha de estado invertida, se invierte el intervalo. Es decir, -1 es bueno y 1 es malo.  
  
 En [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], el nombre del gráfico de KPI determina si el gráfico tiene tres o cinco estados. La tabla siguiente muestra el uso, nombre y el número de Estados que [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] asocia sus gráficos de KPI.  
  
|Uso de gráfico|Nombre del gráfico de KPI.|Número de estados|  
|--------------------|-------------------------|----------------------|  
|Estado|Formas|3|  
|Estado|Semáforo|3|  
|Estado|Señales viales|3|  
|Estado|Medidor|3|  
|Estado|Medidor invertido|5|  
|Estado|Termómetro|3|  
|Estado|Cilindro|3|  
|Estado|Caras|3|  
|Estado|Flecha de varianza|3|  
|Tendencia|Flecha estándar|3|  
|Tendencia|Flecha de estado|3|  
|Tendencia|Flecha de estado invertida|5|  
|Tendencia|Caras|3|  
  
## <a name="see-also"></a>Vea también  
 [Eliminar KPI, instrucción &#40; MDX &#41;](../mdx/mdx-data-definition-drop-kpi.md)   
 [Instrucciones de definición de datos MDX &#40; MDX &#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
