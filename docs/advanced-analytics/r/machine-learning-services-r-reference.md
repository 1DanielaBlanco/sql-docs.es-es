---
title: "Referencia de API de servicios de aprendizaje de máquina de SQL Server | Documentos de Microsoft"
ms.custom: 
ms.date: 10/31/2017
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 52261d7ebb01ca4156d067ba0f25af3cd90a64bb
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="api-reference-for-sql-server-machine-learning-services"></a>Referencia de API de servicios de aprendizaje de máquina de SQL Server

Este artículo contiene vínculos a la documentación de referencia de API que se usan con SQL Server de aprendizaje automático.

**Se aplica a:** servicios de aprendizaje de automático de SQL Server 2016 R Services, SQL Server de 2017

En su mayor parte, SQL Server utiliza las mismas bibliotecas de R y Python que se proporcionan en Microsoft R Server y servidor de aprendizaje de máquina de Microsoft. 

> [!NOTE]
> Documentación para todas las API se deriva de código fuente y no se hayan editado. Si ve errores, agregue un comentario en la documentación de referencia de API. 

## <a name="r"></a>L

+ [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)

    Algoritmos escalables que admiten varios orígenes de datos y contextos de proceso remoto.

+ [MicrosoftML](https://docs.microsoft.com/machine-learning-serverr-reference/microsoftml/microsoftml-package)

    Las transformaciones y los algoritmos de aprendizaje para R. requiere RevoScaleR máquina rápida y escalable.

+ [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr)

   Lee el esquema de orígenes de datos OLAP y ejecuta consultas MDX.

+ [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)

    Funciones auxiliares para generar un procedimiento almacenado correcto desde el código de R.

+ [mrsdeploy](https://docs.microsoft.com/machine-learning-server/r-reference/mrsdeploy/mrsdeploy-package)

   Funciones para establecer una sesión remota en una aplicación de consola y para publicar y administrar un servicio web que usa código de R o Python.

## <a name="python"></a>Python

+ [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package)

    Equivalente de Python del paquete RevoScaleR para el lenguaje R. Es compatible con los mismos orígenes de datos y contextos de proceso.

+ [Microsoftml para Python](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)

    Equivalente de Python de la MicrosoftML del paquete de R. es compatible con los mismos contextos de proceso y orígenes de datos e incluye rápido, algoritmos escalables y transformaciones de Microsoft. 

## <a name="related-apis"></a>API relacionadas

+ [Referencia a la función RevoPEMAR](https://docs.microsoft.com/machine-learning-server/r-reference/revopemar/pemar)

    Admite el desarrollo de algoritmos paralelos

+ [RevoUtils](https://docs.microsoft.com/machine-learning-server/r-reference/revoutils/revoutils)

    Funciones de utilidad para su uso con entornos de RevoScaleR

## <a name="other"></a>Otro

Temas "Cómo" y resúmenes específicas para el uso de estas R o las API de Python en SQL Server pueden encontrarse aquí:

+ [Funciones scaleR para trabajar con SQL Server](scaler-functions-for-working-with-sql-server-data.md)
+ [Generar un procedimiento almacenado mediante sqlrutils](generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)
+ [Leer datos de MDX en R mediante olapR](how-to-create-mdx-queries-using-olapr.md)
