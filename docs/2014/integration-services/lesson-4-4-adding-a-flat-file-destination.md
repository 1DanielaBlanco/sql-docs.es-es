---
title: 'Paso 4: Agregar un destino de archivo plano | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4088de3-16d8-419c-96a1-a2cd005d0a5b
caps.latest.revision: 27
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 00f6cc4f2a6d2283a44b91319362bf0cd171a448
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36114291"
---
# <a name="step-4-adding-a-flat-file-destination"></a>Paso 4: Agregar un destino de archivo plano
  La salida de errores de la transformación Lookup Currency Key redirige a la transformación Script cualquier fila de datos que haya generado un error durante la operación de búsqueda. Para mejorar la información acerca de los errores producidos, la transformación Script ejecuta un script que obtiene una descripción de los errores.  
  
 En esta tarea guardará toda esta información acerca de las filas con errores en un archivo delimitado para su procesamiento posterior. Para guardar las filas con errores, es preciso agregar y configurar un administrador de conexiones de archivos planos para el archivo de texto que contendrá los datos de error y un destino de archivo plano. Al establecer propiedades en el administrador de conexiones de archivos planos que usa el destino de archivo plano, puede especificar la manera en que el destino de archivo plano establece el formato y escribe el archivo de texto. Para obtener más información, vea [Flat File Connection Manager](connection-manager/file-connection-manager.md) y [Flat File Destination](data-flow/flat-file-destination.md).  
  
### <a name="to-add-and-configure-a-flat-file-destination"></a>Para agregar y configurar un destino de archivo plano  
  
1.  Haga clic en la pestaña **Flujo de datos** .  
  
2.  En el **Cuadro de herramientas de SSIS**, expanda **Otros**y arrastre **Destino de archivo plano** a la superficie de diseño del flujo de datos. Coloque el **Destino de archivo plano** directamente debajo de la transformación **Get Error Description** .  
  
3.  Haga clic en la transformación **Get Error Description** y arrastre la flecha verde hasta el nuevo **Destino de archivo plano**.  
  
4.  En la superficie de diseño **Flujo de datos** , haga clic en **Destino de archivo plano** en la transformación **Destino de archivo plano** recién agregada y cambie el nombre a **Failed Rows**.  
  
5.  Haga clic con el botón derecho en la transformación **Failed Rows** , haga clic en **Editar**y, después, en el **Editor de destino de archivos planos**, haga clic en **Nuevo**.  
  
6.  En el cuadro de diálogo **Formato de archivo plano** , compruebe que esté seleccionado **Delimitado** y haga clic en **Aceptar**.  
  
7.  En el **Editor del Administrador de conexión de archivos planos**, en la **nombre de administrador de conexiones** cuadro, escriba `Error Data`.  
  
8.  En el cuadro de diálogo **Editor del administrador de conexiones de archivos planos** , haga clic en **Examinar**y busque la carpeta en la que se almacenará el archivo.  
  
9. En el **abiertos** cuadro de diálogo para **nombre de archivo**, tipo `ErrorOutput.txt`y, a continuación, haga clic en **abiertos**.  
  
10. En el cuadro de diálogo **Editor del administrador de conexiones de archivos planos** , compruebe que el cuadro **Configuración regional** contiene Inglés (Estados Unidos) y la **Página de códigos** contiene 1252 (ANSI -Latin I).  
  
11. En el panel de opciones, haga clic en **Columnas**.  
  
     Observe que, además de las columnas del archivo de datos de origen, existen tres columnas nuevas: ErrorCode, ErrorColumn y ErrorDescription. Estas columnas las generan la salida de errores de la transformación Lookup Currency Key y el script de la transformación Get Error Description y pueden utilizarse para solucionar el problema de la fila que genera el error.  
  
12. Haga clic en **Aceptar**.  
  
13. En el **Editor de destino de archivos planos**, desactive la casilla **Sobrescribir los datos del archivo** .  
  
     Al desactivar esta casilla, se conservan los errores sobre múltiples ejecuciones del paquete.  
  
14. En el **Editor de destino de archivos planos**, haga clic **Asignaciones** para comprobar que todas las columnas son correctas. Si lo desea, puede cambiar el nombre de las columnas en el destino.  
  
15. Haga clic en **Aceptar**.  
  
## <a name="next-steps"></a>Pasos siguientes  
 [Paso 5: Probar el paquete del tutorial de la lección 4](../integration-services/lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
  