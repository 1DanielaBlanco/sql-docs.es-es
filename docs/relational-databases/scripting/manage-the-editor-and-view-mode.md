---
title: "Administrar el editor y el modo de vista | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editor de consultas [SQL Server Management Studio], administrar comportamiento de ventanas"
  - "modos de vista de plataformas de trabajo [SQL Server Management Studio]"
  - "modo de pantalla completa [SQL Server Management Studio]"
  - "fuentes [SQL Server Management Studio]"
  - "ajustes de línea [SQL Server Management Studio]"
  - "modo de espacio virtual [SQL Server Management Studio]"
  - "dividir vistas de documentos"
  - "mostrar números de línea"
  - "modos de vista [SQL Server Management Studio]"
ms.assetid: 25c58a14-9f94-4296-9770-7d84c6bc3969
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Administrar el editor y el modo de vista
  El editor permite controlar la vista del código de diferentes maneras.  
  
## Cambiar el modo de vista  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] incluye un modo de vista denominado **Organización por pestañas**que permite abrir varios editores y documentos al mismo tiempo, y tener acceso a ellos mediante pestañas situadas en la parte superior del editor. También puede abrir el entorno de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] en modo Interfaz de múltiples documentos (MDI) para unir las ventanas sin las pestañas y poder organizarlas en mosaico, minimizarlas, etc.  
  
#### Para cambiar de un modo de vista a otro  
  
1.  En el menú **Herramientas** , haga clic en **Opciones** .  
  
2.  Haga clic en **Entorno**. Haga clic en **General**.  
  
3.  Haga clic en **Organización por pestañas** o **Entorno MDI**.  
  
    > [!NOTE]  
    >  Los cambios no serán efectivos hasta que no se reinicie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## Dividir la vista  
 Una ventana del editor también se puede dividir en dos partes independientes para facilitar la edición.  
  
#### Para dividir una ventana  
  
1.  Haga clic en la barra de división, que está situada encima de la barra de desplazamiento.  
  
2.  Arrastre hacia abajo la barra de división.  
  
3.  Para volver a un solo panel, haga doble clic en la barra de división que divide los dos paneles.  
  
 El nuevo panel contiene el mismo documento y cualquier cambio realizado en un panel se refleja en el otro, siempre que muestre el mismo lugar del documento.  
  
## Ajuste de línea  
 Cuando se activa la opción Ajuste de línea, la barra de desplazamiento horizontal desaparece y las líneas de código que exceden el tamaño de la ventana del editor pasan automáticamente a la línea siguiente en lugar de salirse de la pantalla.  
  
#### Para activar el ajuste de línea  
  
1.  En el menú **Herramientas** , haga clic en **Opciones** .  
  
2.  Haga clic en **Editor de texto**.  
  
3.  Abra la carpeta del idioma correspondiente (o **Todos los idiomas** para seleccionar todos los idiomas).  
  
4.  Seleccione **Ajuste de línea**.  
  
## Habilitar el modo de espacio virtual  
 En el modo de **espacio virtual** , el editor actúa como si el espacio que hay al final de cada línea estuviera lleno de un número infinito de espacios, de manera que las líneas de código continuaran fuera del área visible de la pantalla.  
  
#### Para habilitar el modo de espacio virtual  
  
1.  En el menú **Herramientas** , haga clic en **Opciones** .  
  
2.  Haga clic en **Editor de texto**.  
  
3.  Abra la carpeta del idioma correspondiente (o **Todos los idiomas** para seleccionar todos los idiomas).  
  
4.  Seleccione **Habilitar espacio virtual**.  
  
 Cuando el modo de espacio virtual no está habilitado, el cursor salta del final de una línea al primer carácter de la siguiente y viceversa.  
  
## Mostrar números de línea  
 Se puede activar la numeración de líneas en el código. Los números de línea son muy útiles para navegar por el código. Para obtener más información, vea [Navegar por código y texto](../../relational-databases/scripting/navigate-code-and-text.md).  
  
> [!NOTE]  
>  Aunque se active la numeración de líneas, el documento no se imprimirá con los números de línea. Para que se impriman, debe activar la casilla **Números de línea** en el comando **Configurar página** del menú **Archivo** .  
  
#### Para mostrar los números de línea en el código  
  
1.  En el menú **Herramientas** , haga clic en **Opciones** .  
  
2.  Haga clic en **Editor de texto**.  
  
3.  Haga clic en **Todos los lenguajes**.  
  
4.  Haga clic en **General**.  
  
5.  Active **Números de línea**.  
  
 Para aplicar la numeración de líneas solo a algunos lenguajes de programación, seleccione **Números de línea** en la carpeta correspondiente.  
  
## Habilitar el modo de pantalla completa  
 Habilite el modo Pantalla completa para ocultar todas las ventanas de herramienta y ver solamente las ventanas de documento.  
  
#### Para habilitar el modo de pantalla completa  
  
1.  Presione ALT+MAYÚS+ENTRAR para alternar el modo Pantalla completa.  
  
## Utilizar la opción Ocultar todo automáticamente  
  
#### Para ocultar todas las ventanas de herramientas a la vez  
  
1.  En el menú **Ventana** , active **Ocultar todo automáticamente** .  
  
  