---
title: "Paso 4: Crear características de datos mediante T-SQL | Microsoft Docs"
ms.custom: 
ms.date: 10/17/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2f28400200105e8e63f787cbcda58c183ba00da5
ms.openlocfilehash: aec9f035404cbd08c40d518db576e443b28a210a
ms.contentlocale: es-es
ms.lasthandoff: 10/18/2017

---
# <a name="step-4-create-data-features-using-t-sql"></a>Paso 4: Crear características de datos mediante T-SQL

Después de la exploración de datos, ha recopilado la información de los datos y está listo para mover en *característica ingeniería*. Este proceso de creación de características de los datos sin formato puede ser un paso crítico en análisis avanzados de modelado.

Este artículo forma parte de un tutorial, [análisis de Python en bases de datos para desarrolladores de SQL](sqldev-in-database-python-for-sql-developers.md). 

En este paso, aprenderá a crear características desde datos sin procesar mediante una función de [!INCLUDE[tsql](../../includes/tsql-md.md)] . Después, llamaremos a esa función desde un procedimiento almacenado para crear una tabla que contiene los valores de las características.

## <a name="define-the-function"></a>Definir la función

Los valores de distancia notificados en los datos originales se basan en la distancia notificada del taxímetro y no representan necesariamente la distancia geográfica o la distancia recorrida. Por tanto, debe calcular la distancia directa entre los puntos de origen y destino, usando las coordenadas disponibles en el conjunto de datos de origen NYC Taxi. Puede hacerlo mediante la [fórmula Haversine](https://en.wikipedia.org/wiki/Haversine_formula) en un función personalizada de [!INCLUDE[tsql](../../includes/tsql-md.md)] .

Usará una función personalizada de T-SQL, _fnCalculateDistance_, para calcular la distancia usando la fórmula Haversine, y una segunda función personalizada de T-SQL, _fnEngineerFeatures_, para crear una tabla que contiene todas las características.

### <a name="calculate-trip-distance-using-fncalculatedistance"></a>Calcular la distancia de viaje con fnCalculateDistance

1.  La función _fnCalculateDistance_ debe haberse descargado y registrado con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] como parte de la preparación para este tutorial. Dedique un minuto a revisar el código.
  
    En [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], expanda **Programación**, expanda **Funciones** y, después, **Funciones escalares**.
    Haga clic con el botón derecho en _fnCalculateDistance_y seleccione **Modificar** para abrir el script de [!INCLUDE[tsql](../../includes/tsql-md.md)] en una nueva ventana de consulta.
  
    ```SQL
    CREATE FUNCTION [dbo].[fnCalculateDistance] (@Lat1 float, @Long1 float, @Lat2 float, @Long2 float)
    -- User-defined function that calculates the direct distance between two geographical coordinates
    RETURNS float
    AS
    BEGIN
      DECLARE @distance decimal(28, 10)
      -- Convert to radians
      SET @Lat1 = @Lat1 / 57.2958
      SET @Long1 = @Long1 / 57.2958
      SET @Lat2 = @Lat2 / 57.2958
      SET @Long2 = @Long2 / 57.2958
      -- Calculate distance
      SET @distance = (SIN(@Lat1) * SIN(@Lat2)) + (COS(@Lat1) * COS(@Lat2) * COS(@Long2 - @Long1))
      --Convert to miles
      IF @distance <> 0
      BEGIN
        SET @distance = 3958.75 * ATAN(SQRT(1 - POWER(@distance, 2)) / @distance);
      END
      RETURN @distance
    END
    GO
    ```
**Comentarios:**

- La función es una función escalar y devuelve un único valor de datos de un tipo predefinido.
- Toma los valores de latitud y longitud como entradas, obtenidos de las ubicaciones de origen y destino de los viajes. La fórmula Haversine convierte ubicaciones en radianes y usa esos valores para calcular la distancia directa en millas entre las dos ubicaciones.

Para agregar el valor calculado a una tabla y poder usarlo para entrenar el modelo, deberá usar otra función, _fnEngineerFeatures_.

### <a name="save-the-features-using-fnengineerfeatures"></a>Guarde las características con _fnEngineerFeatures_

1.  Tómese un minuto para revisar el código de la función personalizada de T-SQL, _fnEngineerFeatures_, que debe haberse creado como parte de la preparación para este tutorial.
  
    Esta función es una función con valores de tabla que toma varias columnas como entradas y genera una tabla con varias columnas de características.  El propósito de esta función es crear un conjunto de características para usar en la creación de un modelo. La función _fnEngineerFeatures_ llama a la función de T-SQL creada anteriormente, _fnCalculateDistance_, para obtener la distancia directa entre las ubicaciones de origen y destino.
  
    ```
    CREATE FUNCTION [dbo].[fnEngineerFeatures] (
    @passenger_count int = 0,
    @trip_distance float = 0,
    @trip_time_in_secs int = 0,
    @pickup_latitude float = 0,
    @pickup_longitude float = 0,
    @dropoff_latitude float = 0,
    @dropoff_longitude float = 0)
    RETURNS TABLE
    AS
      RETURN
      (
      -- Add the SELECT statement with parameter references here
      SELECT
        @passenger_count AS passenger_count,
        @trip_distance AS trip_distance,
        @trip_time_in_secs AS trip_time_in_secs,
        [dbo].[fnCalculateDistance](@pickup_latitude, @pickup_longitude, @dropoff_latitude, @dropoff_longitude) AS direct_distance
      )
    GO
    ```
  
2. Para comprobar que esta función funciona, puede usarla para calcular la distancia geográfica de los viajes en los que la distancia medida era 0 pero las ubicaciones de origen y destino eran diferentes.
  
    ```
        SELECT tipped, fare_amount, passenger_count,(trip_time_in_secs/60) as TripMinutes,
        trip_distance, pickup_datetime, dropoff_datetime,
        dbo.fnCalculateDistance(pickup_latitude, pickup_longitude,  dropoff_latitude, dropoff_longitude) AS direct_distance
        FROM nyctaxi_sample
        WHERE pickup_longitude != dropoff_longitude and pickup_latitude != dropoff_latitude and trip_distance = 0
        ORDER BY trip_time_in_secs DESC
    ```
  
    Como puede ver, la distancia notificada por el taxímetro no siempre se corresponde con la distancia geográfica. Se trata de por qué es importante la ingeniería de característica.

En el paso siguiente, aprenderá cómo utilizar estas características de datos para crear y entrenar un modelo de aprendizaje automático con Python.

## <a name="next-step"></a>Paso siguiente

[Paso 5: Entrenar y guardar un modelo de Python mediante T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="previous-step"></a>Paso anterior

[Paso 3: Explorar y visualizar los datos](sqldev-py3-explore-and-visualize-the-data.md)



