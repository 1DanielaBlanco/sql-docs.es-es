---
title: "Lecci&#243;n 3: Transformar datos mediante R (An&#225;lisis detallado de ciencia de datos) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "10/03/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 0327e788-94cc-4a47-933b-7c5c027b9208
caps.latest.revision: 19
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 18
---
# Lecci&#243;n 3: Transformar datos mediante R (An&#225;lisis detallado de ciencia de datos)
El paquete **RevoScaleR** proporciona varias funciones para transformar los datos en distintas fases del análisis:  
  
-   **rxDataStep** puede usarse para crear y transformar subconjuntos de datos.  
  
-   **rxImport** admite la transformación de los datos a medida que se importan a o desde un archivo XDF o una trama de datos en memoria.  
  
-   Aunque no son específicas para el movimiento de datos, las funciones **rxSummary**, **rxCube**, **rxLinMod** y **rxLogit** admiten transformaciones de datos.  
  
En esta sección, aprenderá a usar estas funciones. Comencemos con *rxDataStep*.  
  
## Usar rxDataStep para transformar variables  
La función *rxDataStep* procesa un fragmento de datos cada vez. Para ello, lo lee en un origen de datos y lo escribe en otro. Puede especificar las columnas que se van a transformar, las transformaciones que se van a cargar, etc.  
  
Para que este ejemplo sea interesante, usará una función de otro paquete de R para transformar los datos.  El paquete **boot** es uno de los paquetes "recomendados", lo que significa que **boot** se incluye con todas las distribuciones de R, pero no se carga automáticamente en el inicio. Por lo tanto, el paquete ya debe de estar disponible en la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que ha usado con [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
Desde el paquete **boot**, usará la función *inv.logit* que calcula el inverso de una función logit. Es decir, la función *inv.logit* convierte una función logit a una probabilidad en la escala [0,1].  
  
> [!TIP]  
> Otra manera de obtener predicciones en esta escala sería establecer el parámetro *type* en **response** en la llamada original a *rxPredict*.  
  
1.  Empiece creando un origen de datos para almacenar los datos destinados a la tabla *ccScoreOutput*.  
  
    ```R  
    sqlOutScoreDS <- RxSqlServerData( table =  "ccScoreOutput",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )  
  
    ```  
  
2.  Agregue otro origen de datos para almacenar los datos para la tabla ccScoreOutput2.  
  
    ```R  
    sqlOutScoreDS2 <- RxSqlServerData( table =  "ccScoreOutput2",  connectionString = sqlConnString, rowsPerRead = sqlRowsPerRead )  
  
    ```  
  
    En la tabla nueva, obtendrá todas las variables de la tabla *ccScoreOutput* anterior, además de la variable recién creada.  
  
3.  Establezca el contexto de proceso en la instancia de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    ```R  
    rxSetComputeContext(sqlCompute)  
  
    ```  
  
4.  Use la función *rxSqlServerTableExists* para comprobar si la tabla de salida *ccScoreOutput2* ya existe, y de ser así, use la función *rxSqlServerDropTable* para eliminar la tabla.  
  
    ```R    
    if (rxSqlServerTableExists("ccScoreOutput2"))     rxSqlServerDropTable("ccScoreOutput2")  
  
    ```  
  
5.  Llame a la función *rxDataStep* y especifique las transformaciones deseadas en una lista.  
  
    ```R  
    rxDataStep(inData = sqlOutScoreDS,   
        outFile = sqlOutScoreDS2,         
        transforms = list(ccFraudProb = inv.logit(ccFraudLogitScore)),        
        transformPackages = "boot",   
        overwrite = TRUE)    
    ```  
  
    Al definir las transformaciones que se aplican a cada columna, también puede especificar los paquetes de R adicionales que se necesitan para realizar las transformaciones.  Para obtener más información sobre los tipos de transformaciones que puede realizar, consulte [Transformar y crear un subconjunto de datos](https://msdn.microsoft.com/microsoft-r/scaler-user-guide-data-transform).
  
6.  Llame a *rxGetVarInfo* para ver un resumen de las variables del nuevo conjunto de datos.  
  
    ```R  
    rxGetVarInfo(sqlOutScoreDS2)  
    ```  
  
**Resultado**  
  
*Var 1: ccFraudLogitScore, Type: numeric*  
*Var 2: state, Type: character*  
*Var 3: gender, Type: character*  
*Var 4: cardholder, Type: character*  
*Var 5: balance, Type: integer*  
*Var 6: numTrans, Type: integer*  
*Var 7: numIntlTrans, Type: integer*  
*Var 8: creditLine, Type: integer*  
*Var 9: ccFraudProb, Type: numeric*  
  
Las puntuaciones originales de la función logit se conservan, pero se ha agregado una nueva columna, *ccFraudProb*, en la que las puntuaciones de la función logit se representan como valores comprendidos entre 0 y 1. 

Observe que las variables de factor se han escrito en la tabla *ccScoreOutput2* como datos de caracteres.  Para usarlos como factores en análisis posteriores, use el parámetro *colInfo* para especificar los niveles.  

  
## Paso siguiente  
[Cargar datos en memoria mediante rxImport &#40;Análisis detallado de ciencia de datos&#41;](../../advanced-analytics/r-services/load-data-into-memory-using-rximport-data-science-deep-dive.md)  
  
## Paso anterior  
[Lesson 2: Create and Run R Scripts &#40;Data Science Deep Dive&#41; (Lección 2: Crear y ejecutar scripts de R &#40;Análisis detallado de ciencia de datos&#41;)](../../advanced-analytics/r-services/lesson-2-create-and-run-r-scripts-data-science-deep-dive.md)  
  
  
  
