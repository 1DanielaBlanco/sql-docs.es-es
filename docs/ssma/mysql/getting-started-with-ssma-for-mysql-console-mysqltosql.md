---
title: Introducción a SSMA para la consola de MySQL (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- MySQL Console, launching console
- MySQL Console, output conventions
ms.assetid: 218d502c-059f-4d48-9aea-61e553d74303
caps.latest.revision: 23
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 8f33769bee5c8d6d9e134eb9dd5dcf8549d651cb
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2018
ms.locfileid: "38983087"
---
# <a name="getting-started-with-ssma-for-mysql-console-mysqltosql"></a>Introducción a SSMA para la consola de MySQL (MySQLToSQL)
En esta sección se describe el procedimiento para iniciar y empezar a trabajar con la aplicación de consola de MySQL. También se enumeran en este documento, se utilizan las convenciones en una ventana de salida de la consola SSMA típica.  
  
## <a name="launching-ssma-console"></a>Iniciar la consola SSMA  
Use los pasos siguientes para iniciar la aplicación de consola SSMA:  
  
1.  Vaya a **iniciar** y apuntar a **todos los programas**.  
  
2.  Haga clic en el **SQL Server Migration Assistant para MySQL símbolo del sistema** acceso directo.  
  
    Muestra el menú de uso de la consola SSMA y `(/? Help)`, que le ayudarán a empezar a trabajar con la aplicación de consola.  
  
## <a name="procedure-for-using-the-ssma-console"></a>Procedimiento para usar la consola SSMA  
Después de la consola se inicia correctamente en el sistema de Windows, podría utilizar los pasos siguientes para trabajar en ella:  
  
1.  Configure la consola SSMA a través de los archivos de script. Para obtener más información en esta sección, consulte [crear archivos de Script &#40;MySQLToSQL&#41; ](../../ssma/mysql/creating-script-files-mysqltosql.md) .  
  
2.  [Creación de archivos de valor Variable &#40;MySQLToSQL&#41;](../../ssma/mysql/creating-variable-value-files-mysqltosql.md)  
  
3.  [Creación de los archivos de conexión de servidor &#40;MySQLToSQL&#41;](../../ssma/mysql/creating-the-server-connection-files-mysqltosql.md)  
  
4.  [Ejecución de la consola de SSMA &#40;MySQLToSQL&#41; ](../../ssma/mysql/executing-the-ssma-console-mysqltosql.md) según las necesidades del proyecto  
  
Características adicionales:  
  
1.  [Protección de contraseña](http://msdn.microsoft.com/4ffbc587-ea3f-49ad-bc42-a654f672325e) y exportar / importar en otros equipos de la ventana  
  
2.  [Generar informes](http://msdn.microsoft.com/1c0202e8-546d-4cb3-a37f-1d2e35d53839) ver el xml detallado de salida de informes de evaluación /conversion y migración de datos. También se pueden generar informes de errores detallada para los comandos de actualización y la sincronización.  
  
## <a name="ssma-console-output-conventions"></a>Convenciones de salida de consola SSMA  
Al ejecutar los comandos de script SSMA y opciones, el programa de consola muestra los resultados y mensajes (información, error, etc.) al usuario en la consola o si es necesario, se redirige a un archivo de salida xml. Cada tipo de mensaje en la salida se especifica mediante un color único. Por ejemplo, el mensaje de texto en color blanco indica los comandos del archivo de script; el que aparece en color verde representa un símbolo del sistema de entrada del usuario y así sucesivamente.  
  
![SSMAConsoleOutput_MySQL](../../ssma/mysql/media/ssmaconsoleoutput_mysql.jpg "SSMAConsoleOutput_MySQL")  
  
Interpretación de color de la salida de consola en la tabla siguiente:  
  
|Color|Descripción|  
|---------|---------------|  
|Rojo|Error irrecuperable durante la ejecución|  
|Gris|Marca de fecha y hora, el mensaje al usuario|  
|Blanco|Secuencias de comandos del archivo, tipo de mensaje|  
|Amarillo|Advertencia|  
|Verde|Símbolo del sistema de entrada del usuario|  
|Cian|Guía de inicio, finalización y el resultado de una operación|  
  
## <a name="see-also"></a>Vea también  
[Instalación de SSMA para MySQL](http://msdn.microsoft.com/e89b45bd-59c1-4d23-8bd7-3dafc1947448)  
  
