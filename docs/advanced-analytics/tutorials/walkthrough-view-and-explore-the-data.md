---
title: Ver y explorar los datos mediante SQL (tutorial) | Documentos de Microsoft
ms.custom: 
ms.date: 07/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: d3835d6d-e68b-486d-81a0-81b717cc6134
caps.latest.revision: 33
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: dd20fe12af6f1dcaf378d737961bc2ba354aabe5
ms.openlocfilehash: 3508b4ac9188906a85a272918ae5cabf4628a3eb
ms.contentlocale: es-es
ms.lasthandoff: 10/04/2017

---
# <a name="view-and-explore-the-data-using-sql-walkthrough"></a>Ver y explorar los datos mediante SQL (tutorial)

La exploración de datos es una parte importante del modelado de datos e implica la revisión de resúmenes de objetos de datos que se usarán para el análisis, así como la visualización de datos. En esta lección, le explorar los objetos de datos y generar gráficos, uso [!INCLUDE[tsql](../../includes/tsql-md.md)] y las funciones de R incluidas en [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].

A continuación, generar gráficos para visualizar los datos, con nuevas funciones proporcionadas por paquetes instalados con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].

> [!TIP]
> ¿Ya es un maestro de R?
>   
> Ahora que ha descargado todos los datos y ha preparado el entorno, puede ejecutar el script de R completo en RStudio o cualquier otro entorno, y explorar la funcionalidad por su cuenta. Simplemente abra el archivo RSQL_Walkthrough.R y resalte y ejecute líneas individuales, o ejecute el script completo como una demostración.
>   
> Para obtener explicaciones adicionales de las funciones de RevoScaleR y sugerencias para trabajar con datos de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en R, continúe con el tutorial. Usa exactamente el mismo script.

## <a name="verify-downloaded-data-using-sql-server"></a>Comprobar los datos descargados con SQL Server

En primer lugar, tómese un minuto para asegurarse de que los datos se han cargado correctamente.

1. Conectarse a su [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instancia mediante la herramienta de administración de favoritos de la base de datos, como [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Explorador de servidores de Visual Studio o código de Visual Studio.

2. Seleccione la base de datos que creó y expanda para ver la nueva base de datos, tablas y funciones.
  
    ![rsql_e2e_ssms_newobjects](media/rsql-e2e-ssms-newobjects.PNG)
  
3.  Para comprobar que los datos se carguen correctamente, haga clic en la tabla y seleccione **seleccionar 1000 filas superiores**. La opción de menú ejecuta esta consulta:

    ```SQL
    SELECT TOP 1000 * FROM [dbo].[nyctaxi_sample]
    ```
    Si no ve datos en la tabla, consulte la sección [Solucionar problemas](walkthrough-prepare-the-data.md) del tema anterior.

4. Esta tabla de datos se ha optimizado para cálculos basados en conjunto al agregarle un [índice de almacén](../../relational-databases/indexes/columnstore-indexes-overview.md). Ejecute esta instrucción para generar un resumen rápido en la tabla.

    ```SQL
    SELECT DISTINCT [passenger_count]
        , ROUND (SUM ([fare_amount]),0) as TotalFares
        , ROUND (AVG ([fare_amount]),0) as AvgFares
    FROM [dbo].[nyctaxi_sample]
    GROUP BY [passenger_count]
    ORDER BY  AvgFares DESC
    ````
    En la lección siguiente, generará resúmenes más complejos con R.

## <a name="next-lesson"></a>Lección siguiente

[Resumir datos mediante R](walkthrough-view-and-summarize-data-using-r.md)

## <a name="previous-lesson"></a>Lección anterior

[Preparar los datos de uso de PowerShell](walkthrough-prepare-the-data.md)

