---
title: 'Paso 6: Agregar y configurar transformaciones de búsqueda | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2016
ms.assetid: 5c59f723-9707-4407-80ae-f05f483cf65f
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 57cadee90ac69a76942c6b3c763ffb9900c4f8d8
ms.sourcegitcommit: 7d2b34c64f97206861ec9ad8d6a6201ac20a4af1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/20/2018
ms.locfileid: "36297411"
---
# <a name="lesson-1-6---adding-and-configuring-the-lookup-transformations"></a>Lección 1-6: Agregar y configurar transformaciones de búsqueda
Tras configurar el origen de archivo plano para extraer datos del archivo de origen, la siguiente tarea consiste en definir las transformaciones de búsqueda necesarias para obtener los valores para las claves **CurrencyKey** y **DateKey**. Una transformación Búsqueda realiza una búsqueda combinando datos de la columna de entrada especificada en una columna de un conjunto de datos de referencia. El conjunto de datos de referencia puede ser una tabla o una vista existente, una tabla nueva o el resultado de una instrucción SQL. En este tutorial, la transformación Búsqueda utiliza un administrador de conexiones OLE DB para conectar con la base de datos que contiene los datos que constituyen el origen del conjunto de datos de referencia.  
  
> [!NOTE]  
> También puede configurar la transformación de Búsqueda para conectar con una caché que contiene el conjunto de datos de referencia. Para más información, consulte [Lookup Transformation](../integration-services/data-flow/transformations/lookup-transformation.md).  
  
Para este tutorial, agregará y configurará los dos componentes de la transformación Búsqueda en el paquete:  
  
-   Una transformación para realizar una búsqueda de valores de la columna **CurrencyKey** de la tabla de dimensiones **DimCurrency** basada en la coincidencia de valores de la columna **CurrencyID** del archivo plano.  
  
-   Una transformación para realizar una búsqueda de valores de la columna **DateKey** de la tabla de dimensiones **DimDate** basada en la coincidencia de valores de la columna **CurrencyDate** del archivo plano.  
  
En ambos casos, la transformación de búsqueda usará el administrador de conexiones OLE DB creado anteriormente.  
  
### <a name="to-add-and-configure-the-lookup-currency-key-transformation"></a>Para agregar y configurar la transformación Lookup Currency Key  
  
1.  En el **cuadro de herramientas de SSIS**, expanda **Comunes**y arrastre **Búsqueda** a la superficie de diseño de la pestaña **Flujo de datos** . Coloque Búsqueda directamente bajo el origen **Extract Sample Currency Data** .  
  
2.  Haga clic en el origen de archivo plano **Extract Sample Currency Data** y arrastre la flecha azul a la transformación **Búsqueda** que acaba de agregar para conectar los dos componentes.  
  
3.  En la superficie de diseño **Flujo de datos** , haga clic en **Búsqueda** en la transformación **Búsqueda** y cambie el nombre por **Lookup Currency Key**.  
  
4.  Haga doble clic en la transformación **Lookup CurrencyKey** para mostrar el Editor de transformación Búsqueda.  
  
5.  En la página **General** , realice las selecciones siguientes:  
  
    1.  Seleccione **Caché completa**.  
  
    2.  En el área **Tipo de conexión** , seleccione **Administrador de conexiones OLE DB**.  
  
6.  En la página **Conexión** , realice las selecciones siguientes:  
  
    1.  En el cuadro de diálogo **Administrador de conexiones OLE DB** , asegúrese de que se muestra **localhost.AdventureWorksDW2012** .  
  
    2.  Seleccione **Usar los resultados de una consulta SQL**y, a continuación, escriba o copie la instrucción SQL siguiente:  
  
        ```sql
        SELECT * FROM [dbo].[DimCurrency]
        WHERE [CurrencyAlternateKey]
        IN ('ARS', 'AUD', 'BRL', 'CAD', 'CNY',
            'DEM', 'EUR', 'FRF', 'GBP', 'JPY',
            'MXN', 'SAR', 'USD', 'VEB')
        ```  
  
7.  En la página **Columnas** , realice las selecciones siguientes:  
  
    1.  En el panel **Columnas de entrada disponibles** , arrastre **CurrencyID** al panel **Columnas de búsqueda disponibles** y suéltelo en **CurrencyAlternateKey**.  
  
    2.  En la lista **Columnas de búsqueda disponibles** , active la casilla situada a la izquierda de **CurrencyKey**.  
  
8.  Haga clic en **Aceptar** para volver a la superficie de diseño **Flujo de datos** .  
  
9. Haga clic con el botón derecho en la transformación Lookup Currency Key y haga clic en **Propiedades**.  
  
10. En la ventana Propiedades, compruebe que la propiedad **LocaleID** esté establecida en **Inglés (Estados Unidos)** y la propiedad **DefaultCodePage** en **1252**.  
  
### <a name="to-add-and-configure-the--lookup-datekey-transformation"></a>Para agregar y configurar la transformación Lookup Date Key  
  
1.  En el **cuadro de herramientas de SSIS**, arrastre **Búsqueda** a la superficie de diseño **Flujo de datos** . Coloque Búsqueda justo debajo de la transformación **Lookup Currency Key** .  
  
2.  Haga clic en la transformación **Lookup Currency Key** y arrastre la flecha verde hasta la transformación **Búsqueda** que acaba de agregar para conectar los dos componentes.  
  
3.  En el cuadro de diálogo **Selección de entrada y salida** , en el cuadro de lista **Salida** , haga clic en **Salida de entradas coincidentes de búsqueda** y, a continuación, haga clic en **Aceptar**.  
  
4.  En la superficie de diseño **Flujo de datos** , haga clic en **Búsqueda** en la transformación **Búsqueda** recién agregada y cambie el nombre por **Lookup Date Key**.  
  
5.  Haga doble clic en la transformación **Lookup Date Key** .  
  
6.  En la página **General** , seleccione **Caché parcial**.  
  
7.  En la página **Conexión** , realice las selecciones siguientes:  
  
    1.  En el cuadro de diálogo **Administrador de conexiones OLEDB** , asegúrese de que se muestra **localhost.AdventureWorksDW2012** .  
  
    2.  En el cuadro **Usar una tabla o vista** , escriba o seleccione **[dbo].[DimDate]**.  
  
8.  En la página **Columnas** , realice las selecciones siguientes:  
  
    1.  En el panel **Columnas de entrada disponibles** , arrastre **CurrencyDate** al panel **Columnas de búsqueda disponibles** y suéltelo en **FullDateAlternateKey**.  
  
    2.  En la lista **Columnas de búsqueda disponibles** , active la casilla situada a la izquierda de **DateKey**.  
  
9. En la página **Avanzadas** , revise las opciones de almacenamiento en memoria caché.  
  
10. Haga clic en **Aceptar** para volver a la superficie de diseño **Flujo de datos** .  
  
11. Haga clic con el botón derecho en la transformación Lookup Date Key y haga clic en **Propiedades.**  
  
12. En la ventana Propiedades, compruebe que la propiedad **LocaleID** esté establecida en **Inglés (Estados Unidos)** y la propiedad **DefaultCodePage** en **1252**.  
  
## <a name="next-task-in-lesson"></a>Siguiente tarea de la lección  
[Paso 7: Agregar y configurar el destino de OLE DB](../integration-services/lesson-1-7-adding-and-configuring-the-ole-db-destination.md)  
  
## <a name="see-also"></a>Ver también  
[Lookup Transformation](../integration-services/data-flow/transformations/lookup-transformation.md)  
  
  
  
