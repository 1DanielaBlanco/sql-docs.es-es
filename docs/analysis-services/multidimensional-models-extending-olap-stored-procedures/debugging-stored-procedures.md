---
title: Depurar procedimientos almacenados | Documentos de Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- debugging stored procedures [Analysis Services]
- stored procedures [Analysis Services], debugging
ms.assetid: 34f51b85-02b3-40dd-bf93-375a9e522385
caps.latest.revision: "26"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7b605ee9a2af577048c03d406ff628b1d279a68e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="debugging-stored-procedures"></a>Depurar procedimientos almacenados
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] los procedimientos almacenados son realmente CLR o COM bibliotecas (generalmente dll) que se escriben en C# (o cualquier otro lenguaje CLR o COM). Por consiguiente, la depuración de un procedimiento almacenado es muy similar a la depuración de cualquier otra aplicación del entorno de depuración de Visual Studio. Los procedimientos almacenados del entorno de desarrollo de Visual Studio pueden depurarse con las funciones de depuración integradas. Con ellas podrá detenerse en ubicaciones de procedimientos, inspeccionar los valores de memoria y registro, cambiar variables, observar el tráfico de mensajes y examinar cómo funciona el código.  
  
### <a name="to-debug-a-stored-procedure"></a>Para depurar un procedimiento almacenado  
  
1.  Abra el proyecto utilizado para crear la DLL en Visual Studio.  
  
2.  Cree puntos de interrupción en el método o función correspondiente al procedimiento que desee depurar.  
  
3.  Utilice Visual Studio para crear una compilación de depuración de una DLL del procedimiento almacenado.  
  
4.  Implemente la DLL en el servidor. Para obtener más información sobre cómo implementar el archivo DLL en el servidor, consulte [crear procedimientos almacenados](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/creating-stored-procedures.md).  
  
5.  Se necesita una aplicación que llame al procedimiento almacenado que desee probar. Si no dispone de una, puede utilizar el Editor de consultas MDX de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] para crear una consulta MDX que llame al procedimiento almacenado que desee probar.  
  
6.  En Visual Studio, adjunte al proceso de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (Msmdsrv.exe).  
  
    1.  Desde el **depurar** menú, elija **toProcess asociar**.  
  
    2.  En el **asociar toProcess** cuadro de diálogo, seleccione **Mostrar procesos de todos los usuarios**.  
  
    3.  En el **procesos disponibles** lista el **proceso** columna, haga clic en **Msmdsrv.exe**. Si se ejecutase más de una instancia de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en el servidor, necesita identificar el proceso mediante el Id. de la instancia que desee utilizar.  
  
    4.  En el **adjuntar a** texto cuadro, asegúrese de que está seleccionado el tipo de programa adecuado. Para una DLL de CLR, haga clic en **seleccione**, a continuación, haga clic en **depurar estos tipos de código**, a continuación, haga clic en **administrada**, a continuación, haga clic en **Aceptar**. Para una DLL de COM, haga clic en **seleccione**, a continuación, haga clic en **depurar estos tipos de código**, a continuación, haga clic en **nativo**, a continuación, haga clic en **Aceptar**.  
  
    5.  Haga clic en **adjuntar**.  
  
7.  En [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], invoque el programa o el script MDX que llama al procedimiento almacenado. El depurador se interrumpirá al alcanzar una línea que contiene un punto de interrupción. Podrá evaluar variables en la ventana de inspección, ver variables locales y reproducir el código.  
  
 Si experimenta problemas al depurar una biblioteca, compruebe que el archivo de la base de datos del programa (PDB) correspondiente se ha copiado en la ubicación de implementación del servidor. Si no se ha copiado el archivo durante el registro o la implementación, es necesario copiarlo manualmente en la misma ubicación que la DLL. En el código nativo (DLL de COM), el archivo PDB reside en el subdirectorio \debug. En el código administrado (DLL de CLR), reside en el subdirectorio \WINDEBUG.  
  
## <a name="see-also"></a>Vea también  
 [Administración de ensamblados de modelos multidimensionales](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Definición de procedimientos almacenados](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
