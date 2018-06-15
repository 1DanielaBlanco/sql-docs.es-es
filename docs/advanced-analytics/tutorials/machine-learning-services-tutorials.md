---
title: Tutoriales de servicios de aprendizaje de máquina SQL Server | Documentos de Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 604bbe9eb2a28c32b862174ce5da9cc5092e0c64
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31203757"
---
# <a name="tutorials-for-sql-server-machine-learning-services"></a>Tutoriales de servicios de aprendizaje de máquina SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Este artículo proporciona una lista completa de los tutoriales, demostraciones y las aplicaciones de ejemplo que utilizan características de aprendizaje de máquina de SQL Server 2016 o 2017 de SQL Server. Empiece aquí para obtener información sobre cómo ejecutar R o Python de T-SQL, cómo usar contextos de proceso local y remota y cómo optimizar el código R y Python para un entorno de producción de SQL.

## <a name="start-here"></a>Comenzar aquí

+ [Tutoriales de Python](../tutorials/sql-server-python-tutorials.md)

+ [Tutoriales de R](../tutorials/sql-server-r-tutorials.md)

Para obtener más información sobre los requisitos y cómo configurarlas, consulte [requisitos previos](#bkmk_prerequisites).

## <a name="samples-and-solutions"></a>Ejemplos y soluciones

+ [Ejemplos](#bkmk_samples) 

    Estas situaciones del mundo real en el equipo de desarrollo de SQL Server, muestran cómo incrustar el aprendizaje automático en las aplicaciones. Todos los ejemplos incluyen código que puede descargar, modificar y utilizar en producción.

+ [Soluciones](#bkmk_solutions) 

    Plantillas desde el equipo de ciencia de datos de Microsoft son personalizables, para que pueda empezar rápidamente con aprendizaje automático. Cada solución se adapta a un problema de tarea o un sector específico. La mayoría de las soluciones está diseñada para ejecutarse en SQL Server, o en un entorno de nube, como el aprendizaje automático de Azure. Otras soluciones pueden ejecutar en Linux o en clústeres Spark o Hadoop, mediante Microsoft R Server o servidor de aprendizaje de máquina.

### <a name ="bkmk_samples"></a>Muestras de productos de SQL Server

Estos ejemplos y demostraciones proporcionadas por el equipo de desarrollo de SQL Server y servidor de R resalte formas en que puede utilizar análisis incrustado en las aplicaciones reales.

+ [Realizar cliente agrupación en clústeres mediante R y SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/)

  Usar aprendizaje supervisado a los clientes de segmento basándose en los datos de ventas. En este ejemplo se usa el algoritmo de rxKmeans escalables de Microsoft R para generar el modelo de agrupación en clústeres. 
  
  Se aplica a: SQL Server 2016 o SQL Server de 2017

+ [¡NUEVO! Realizar cliente agrupación en clústeres mediante Python y SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/)

    Obtenga información acerca de cómo usar el algoritmo Kmeans para realizar la agrupación en clústeres supervisados de clientes. Este ejemplo utiliza la Python lenguaje en bases de datos.
    
    Se aplica a: SQL Server de 2017

+ [Crear un modelo de predicción con R y SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction)

  Obtenga información acerca de cómo una empresa de alquiler de ski puede usar el aprendizaje automático para predecir alquileres futuras, que le permite el plan de negocios y el personal para satisfacer la demanda futura. Este ejemplo usa los algoritmos de Microsoft para compilar la regresión logística y los modelos de árboles de decisión. 
  
  Se aplica a: SQL Server 2016 o SQL Server de 2017

+ [Crear un modelo de predicción mediante Python y SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

   Compile la aplicación de análisis de alquiler de ski con Python, para ayudarle a planear la demanda futura. Este ejemplo utiliza la nueva biblioteca de Python, **revoscalepy**, para crear un modelo de regresión lineal.
   
   Se aplica a: SQL Server de 2017

+ [Cómo usar una plantilla con servicios de aprendizaje de máquina de SQL Server](https://blogs.msdn.microsoft.com/mlserver/2017/12/14/how-to-use-tableau-with-sql-server-machine-learning-services-with-r-and-python/)

    Analizar los medios sociales y crear gráficos de Tableau, con SQL Server y R.

### <a name="bkmk_solutions"></a>Plantillas de solución

El equipo de ciencia de datos de Microsoft ha proporcionado plantillas de solución que pueden usarse para impulsar soluciones para escenarios comunes. Se proporciona todo el código, así como instrucciones sobre cómo entrenar e implementar un modelo para puntuar utilizando procedimientos almacenados de SQL Server.

+ [Detección de fraude](https://gallery.cortanaanalytics.com/Tutorial/Online-Fraud-Detection-Template-with-SQL-Server-R-Services-1)
+ [Predicción personalizada de abandono](https://gallery.cortanaanalytics.com/Tutorial/Customer-Churn-Prediction-Template-with-SQL-Server-R-Services-1)
+ [Mantenimiento predictivo](https://gallery.cortanaanalytics.com/Tutorial/Predictive-Maintenance-Template-with-SQL-Server-R-Services-1)
+ [Predecir longitud hospital permanencia](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

Para obtener más información, consulte [Plantillas de aprendizaje automático con SQL Server 2016 R Services](https://blogs.technet.microsoft.com/machinelearning/2016/03/23/machine-learning-templates-with-sql-server-2016-r-services/).

## <a name="more-resources-and-reading"></a>Más recursos y lectura

+ [¿Por qué genérelo?](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/01/10/sql-server-r-services-why-did-we-build-it/)

    ¿Quiere conocer la verdadera historia tras R Services? Lea este artículo desde el equipo de desarrollo y PM que explica el origen y los objetivos de SQL Server R Services.

+ [Tutoriales y los datos de ejemplo de Microsoft R](https://docs.microsoft.com/machine-learning-server/r/tutorial-introduction)

    Obtenga información sobre Microsoft R y lo que el paquete RevoScaleR que ofrece en esta serie de tutoriales rápidos. Obtener información sobre cómo escribir código en R una vez e implementar en cualquier lugar, con RevoScaleR orígenes de datos y contextos de proceso remoto.

+ [Empezar a trabajar con MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package)

  Obtenga información acerca de cómo usar los nuevos algoritmos en el paquete MicrosoftML para avanzadas de modelado y transformaciones de datos escalable, optimizadas para varios contextos de proceso.

## <a name="bkmk_Prerequisites"></a>Requisitos previos

Para ejecutar estos tutoriales, debe descargar e instalar los componentes, de aprendizaje de automático de SQL Server como se describe aquí:

+ [Instalar servicios de aprendizaje automático SQL Server de 2017 (en bases de datos)](../install/sql-machine-learning-services-windows-install.md)
+ [Instalar SQL Server 2016 R Services (en bases de datos)](../install/sql-r-services-windows-install.md)

Con SQL Server 2017, puede instalar R, Python o ambos. En caso contrario, el proceso de instalación de general, la arquitectura y los requisitos son los mismos.

Después de ejecutar el programa de instalación de SQL Server, no olvide estos pasos importantes:

1. Habilitar la característica de ejecución de script externo mediante la ejecución de `sp_configure 'external scripts enabled', 1`. Siga las instrucciones para volver a configurar y reinicie SQL Server.
2. Asegúrese de que se está ejecutando el servicio Launchpad, y que las cuentas de trabajo Launchpad pueden conectarse a la instancia de SQL Server.
3. Revise los permisos asociados a los usuarios que deben ejecutar scripts de R o Python. Independientemente de si utiliza los inicios de sesión SQL o cuentas de usuario de Windows, el usuario debe tener permiso para ejecutar scripts de R o Python y debe ser capaz de conectarse a la instancia. Según el tutorial, el usuario también podría requerir permiso para escribir datos, crear objetos de base de datos o realizar una masiva importación de datos.

Para obtener más información, consulte este artículo para algunos problemas comunes de instalación y configuración: [solución de problemas de servicios de aprendizaje de máquina](../machine-learning-troubleshooting-faq.md)

> [!NOTE]
> No se puede ejecutar estos tutoriales usar otra herramienta de código abierto R o Python. El entorno de desarrollo y el equipo de SQL Server con aprendizaje automático deben tener las bibliotecas R o Python suministradas por Microsoft, que admiten la integración con SQL Server y el uso de contextos de proceso remoto.
