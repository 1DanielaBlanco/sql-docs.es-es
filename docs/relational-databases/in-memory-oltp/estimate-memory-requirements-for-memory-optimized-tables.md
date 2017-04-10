---
title: "Estimar los requisitos de memoria para las tablas con optimizaci&#243;n para memoria | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5c5cc1fc-1fdf-4562-9443-272ad9ab5ba8
caps.latest.revision: 32
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 32
---
# Estimar los requisitos de memoria para las tablas con optimizaci&#243;n para memoria
[!INCLUDE[tsql-appliesto-ss2014-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-asdb-xxxx-xxx-md.md)]

Las tablas con optimización para memoria requieren que exista memoria suficiente para mantener todas las filas e índices en memoria. Dado que la memoria es un recurso finito, es importante que conozca y administre el uso que hace de la memoria en su sistema. Los temas de esta sección se ocupan de situaciones de uso y administración de la memoria.

Si va a crear una nueva tabla con optimización para memoria o va a migrar una tabla basada en disco existente a una tabla con optimización para memoria de [!INCLUDE[hek_2](../../includes/hek-2-md.md)], es importante tener una estimación razonable de las necesidades de memoria de cada tabla para que puede aprovisionar el servidor con la memoria adecuada. En esta sección se describe cómo calcular la cantidad de memoria necesaria para almacenar los datos de una tabla con optimización para memoria.  
  
Si va a realizar la migración desde tablas basadas en disco a tablas con optimización para memoria, antes de continuar en este tema, vea el tema [Determinar si una tabla o un procedimiento almacenado se debe pasar a OLTP en memoria](../../relational-databases/in-memory-oltp/determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md) para obtener información sobre qué tablas son más adecuadas para la migración. Todos los temas de [Migrar a OLTP en memoria](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md) ofrecen instrucciones sobre la migración de tablas basadas en disco a tablas con optimización para memoria. 
  
## <a name="basic-guidance-for-estimating-memory-requirements"></a>Instrucciones básicas para estimar los requisitos de memoria

A partir de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], no existe límite en el tamaño de las tablas con optimización para memoria, aunque estas deben adaptarse a la memoria.  En [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], el tamaño de datos admitido es de 256 GB para las tablas SCHEMA_AND_DATA.

El tamaño de una tabla con optimización para memoria corresponde al tamaño de los datos más alguna sobrecarga de los encabezados de fila. Al migrar una tabla basada en disco a una con optimización para memoria, el tamaño de la tabla con optimización para memoria corresponderá aproximadamente al tamaño del índice agrupado o al montón de la tabla original basada en disco.

Los índices de las tablas con optimización para memoria tienden a ser más pequeños que los índices no agrupados de las tablas basadas en disco. El tamaño de los índices no agrupados está en el orden de `[primary key size] * [row count]`. El tamaño de los índices de hash es `[bucket count] * 8 bytes`. 

Cuando existe una carga de trabajo activa, se necesita tener en cuenta la memoria adicional para las versiones de fila y para diversas operaciones. La cantidad de memoria que se necesita en la práctica depende de la carga de trabajo, pero para no tener problemas la recomendación es empezar con dos veces el tamaño esperado de las tablas e índices con optimización para memoria y observar cuáles son los requisitos de memoria en realidad. La sobrecarga de las versiones de fila siempre depende de las características de la carga de trabajo; especialmente las transacciones de larga ejecución aumentan la sobrecarga. Para la mayoría de cargas de trabajo que usan bases de datos más grandes (por ejemplo, más de 100 GB), la sobrecarga tiende a limitarse (25 % o menos).

  
## <a name="detailed-computation-of-memory-requirements"></a>Cálculo detallado de los requisitos de memoria 
  
- [Tabla con optimización para memoria de ejemplo](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md#bkmk_ExampleTable)  
  
- [Memoria para la tabla](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md#bkmk_MemoryForTable)  
  
- [Memoria para índices](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md#bkmk_IndexMeemory)  
  
- [Memoria para versiones de fila](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md#bkmk_MemoryForRowVersions)  
  
- [Memoria para variables de tabla](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md#bkmk_TableVariables)  
  
- [Memoria para el crecimiento](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md#bkmk_MemoryForGrowth)  
  
###  <a name="a-namebkmkexampletablea-example-memory-optimized-table"></a><a name="bkmk_ExampleTable"></a> Tabla con optimización para memoria de ejemplo  

Considere el esquema de tabla con optimización para memoria siguiente:
  
```tsql  
CREATE TABLE t_hk
(  
  col1 int NOT NULL  PRIMARY KEY NONCLUSTERED,  

  col2 int NOT NULL  INDEX t1c2_index   
      HASH WITH (bucket_count = 5000000),  

  col3 int NOT NULL  INDEX t1c3_index   
      HASH WITH (bucket_count = 5000000),  

  col4 int NOT NULL  INDEX t1c4_index   
      HASH WITH (bucket_count = 5000000),  

  col5 int NOT NULL  INDEX t1c5_index NONCLUSTERED,  

  col6 char (50) NOT NULL,  
  col7 char (50) NOT NULL,   
  col8 char (30) NOT NULL,   
  col9 char (50) NOT NULL  

  WITH (memory_optimized = on)  
);
GO  
```  

Con este esquema determinaremos la memoria mínima necesaria para esta tabla con optimización para memoria.  
  
###  <a name="a-namebkmkmemoryfortablea-memory-for-the-table"></a><a name="bkmk_MemoryForTable"></a> Memoria para la tabla  

Una fila de una tabla con optimización para memoria consta de tres partes:
  
- **Marcas de tiempo**   
    Encabezado de fila/marcas de tiempo = 24 bytes.  
  
- **Punteros de índice**   
    Para cada índice hash de la tabla, cada fila tiene un puntero de direcciones de 8 bytes a la siguiente fila del índice.  Puesto que hay 4 índices, cada fila asignará 32 bytes para los punteros de índice (un puntero de 8 bytes para cada índice).  
  
- **Datos**   
    El tamaño de la parte de datos de la fila se determina sumando el tamaño del tipo de cada columna de datos.  En nuestra tabla tenemos cinco enteros de 4 bytes, tres columnas de caracteres de 50 bytes y una columna de caracteres de 30 bytes.  Por tanto, la parte de datos de cada fila es 4 + 4 + 4 + 4 + 4 + 50 + 50 + 30 + 50 o 200 bytes.  
  
A continuación se muestra un cálculo de tamaño para 5.000.000 filas (5 millones de filas) en una tabla con optimización para memoria: La memoria total utilizada por las filas de datos se calcula de la forma siguiente:  
  
#### <a name="memory-for-the-tables-rows"></a>Memoria para las filas de la tabla  
  
Según se desprende de los cálculos anteriores, el tamaño de cada fila de la tabla con optimización para memoria es 24 + 32 + 200, o 256 bytes.  Como tenemos 5 millones de filas, la tabla usará 5 000 000 * 256 bytes, o 1 280 000 000 bytes, aproximadamente 1,28 GB.  
  
###  <a name="a-namebkmkindexmeemorya-memory-for-indexes"></a><a name="bkmk_IndexMeemory"></a> Memoria para índices  

#### <a name="memory-for-each-hash-index"></a>Memoria para cada índice hash  
  
Cada índice hash es una matriz hash de punteros de direcciones de 8 bytes.  El tamaño de la matriz se determina mejor con el número de valores de índice único para ese índice; por ejemplo, el número de valores únicos Col2 es un buen punto de partida para el tamaño de matriz de t1c2_index. Una matriz hash que es demasiado grande desperdicia memoria.  Una matriz hash que es demasiado pequeña reduce el rendimiento, ya que habrá demasiadas colisiones de valores de índice que aplican el algoritmo hash al mismo índice.  
  
Los índices hash consiguen búsquedas de igualdad muy rápidas, por ejemplo:  
  
```tsql  
SELECT * FROM t_hk  
   WHERE Col2 = 3;
```  
  
Los índices no clúster son más rápidos para búsquedas de intervalo como:  
  
```tsql  
SELECT * FROM t_hk  
   WHERE Col2 >= 3;
```  
  
Si va a migrar una tabla basada en disco, puede usar lo siguiente para determinar el número de valores únicos para el índice t1c2_index.  
  
```tsql
SELECT COUNT(DISTINCT [Col2])  
  FROM t_hk;
```  
  
Si va a crear una tabla nueva, necesitará estimar el tamaño de la matriz o recopilar datos de la prueba antes de la implementación.  
  
Para obtener información sobre cómo funcionan los índices de hash en las tablas con optimización para memoria de [!INCLUDE[hek_2](../../includes/hek-2-md.md)], vea [Indexes for Memory-Optimized Tables (Índices para tablas con optimización para memoria)](../Topic/Hash%20Indexes.md).  
  
#### <a name="setting-the-hash-index-array-size"></a>Establecer el tamaño de la matriz de índices hash  
  
El tamaño de la matriz hash se establece mediante `(bucket_count= value)` donde `value` es un valor entero mayor que cero. Si `value` no es una potencia de 2, el valor real de bucket_count se redondea a la siguiente potencia más cercana de 2.  En la tabla de ejemplo (bucket_count = 5000000), como 5 000 000 no es una potencia de 2, el número de depósitos real se redondea hasta 8 388 608 (2^23).  Debe usar este número, no 5.000.000, al calcular la memoria necesaria para la matriz hash.  
  
Así, en nuestro ejemplo, la memoria necesaria para cada matriz hash es:  
  
8 388 608 * 8 = 2^23 \* 8 = 2^23 \* 2^3 = 2^26 = 67 108 864 o, aproximadamente, 64 MB.  
  
Puesto que tenemos tres índices hash, la memoria necesaria para los índices hash es 3 * 64 MB = 192 MB.  
  
#### <a name="memory-for-non-clustered-indexes"></a>Memoria para los índices no clúster  
  
Los índices no clúster se implementan como árboles b donde los nodos internos contienen el valor de índice y punteros a los nodos posteriores.  Los nodos hoja contienen el valor de índice y un puntero a la fila de la tabla en memoria.  
  
A diferencia de los índices hash, los índices no clúster no tienen un tamaño de cubo fijo. El índice aumenta y disminuye dinámicamente con los datos.  
  
La memoria que necesitan los índices no clúster se puede calcular de la manera siguiente:  
  
- **Memoria asignada a los nodos no hoja**   
    Para una configuración típica, la memoria asignada a los nodos no hoja es un porcentaje muy pequeño de la memoria total usada por el índice. Es tan pequeña que se puede omitir de forma segura.  
  
- **Memoria para los nodos hoja**   
    Los nodos hoja tienen un fila por cada clave única de la tabla que apunta a las filas de datos con esa clave única.  Si tiene varias filas con la misma clave (es decir, tiene un índice no clúster que no es único), solo hay una fila en el nodo hoja del índice que apunta a una de las filas con las demás filas vinculadas entre sí.  Así, se puede calcular aproximadamente la memoria total necesaria de esta forma:
  - memoryForNonClusteredIndex = (pointerSize + sum (keyColumnDataTypeSizes)) * rowsWithUniqueKeys  
  
 Los índices no clúster son los más adecuados cuando se emplean para búsquedas de intervalo, como se ilustra en la consulta siguiente:  
  
```tsql  
SELECT * FRON t_hk  
   WHERE c2 > 5;  
```  
  
###  <a name="a-namebkmkmemoryforrowversionsa-memory-for-row-versioning"></a><a name="bkmk_MemoryForRowVersions"></a> Memoria para versiones de fila

Para evitar bloqueos, OLTP en memoria emplea simultaneidad optimista al actualizar o eliminar filas. Esto significa que cuando se actualiza una fila, se crea una versión adicional de la fila. Además, las eliminaciones se realizan de manera lógica: la fila existente se marca como eliminada, pero no se quita de inmediato. El sistema conserva versiones de filas anteriores (incluidas las filas eliminadas) disponibles hasta que finaliza la ejecución de todas las transacciones que podrían usar la versión. 
  
Puesto que en cualquier momento puede haber varias filas adicionales en memoria que esperan que el ciclo de recopilación de elementos no utilizados libere su memoria, debe tener la memoria adecuada para admitir estas filas adicionales.  
  
Se puede estimar el número de filas adicionales calculando el número máximo de actualizaciones y eliminaciones de filas por segundo, y multiplicando después ese valor por el número de segundos que tarda la transacción más larga (mínimo de 1).  
  
A continuación, se multiplica ese valor por el tamaño de fila para obtener el número de bytes necesarios para las versiones de fila.  
  
`rowVersions = durationOfLongestTransctoinInSeconds * peakNumberOfRowUpdatesOrDeletesPerSecond`  
  
Las necesidades de memoria para las filas obsoletas se calculan después multiplicando el número de filas obsoletas por el tamaño de una fila de una tabla con optimización para memoria (vea [Memoria para la tabla](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md#bkmk_MemoryForTable) anteriormente).  
  
`memoryForRowVersions = rowVersions * rowSize`  
  
###  <a name="a-namebkmktablevariablesa-memory-for-table-variables"></a><a name="bkmk_TableVariables"></a> Memoria para variables de tabla
  
La memoria usada para una variable de tabla solo se libera cuando la variable de tabla sale del ámbito. Las filas eliminadas, incluidas las filas eliminadas como parte de una actualización, de una variable de tabla no están sujetas a recolección de elementos no utilizados. No se libera memoria hasta que la variable de tabla no sale del ámbito.  
  
Las variables de tabla definidas en un lote de SQL de gran tamaño, en comparación con un ámbito de procedimiento, que se usan en muchas transacciones, pueden consumir mucha memoria. Como no se eliminan mediante el recolector de elementos no utilizados, las filas eliminadas de una variable de tabla pueden usar mucha memoria y disminuir el rendimiento porque las operaciones de lectura deben examinar más allá de las filas eliminadas.  
  
###  <a name="a-namebkmkmemoryforgrowtha-memory-for-growth"></a><a name="bkmk_MemoryForGrowth"></a> Memoria para el crecimiento

Los cálculos anteriores estiman sus necesidades de memoria para la tabla tal y como es actualmente. Además de esta memoria, debe calcular el crecimiento de la tabla y proporcionar la memoria adecuada para permitir ese crecimiento.  Por ejemplo, si prevé un crecimiento del 10 %, necesita multiplicar los resultados anteriores por 1,1 para obtener la memoria total necesaria para la tabla.  
  
## <a name="see-also"></a>Vea también

[Migrar a OLTP en memoria](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
