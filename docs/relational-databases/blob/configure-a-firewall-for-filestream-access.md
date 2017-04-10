---
title: "Configurar un Firewall para el acceso de FILESTREAM | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-blob"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Firewall de Windows [motor de base de datos], FILESTREAM"
  - "FILESTREAM [SQL Server], Firewall de Windows"
ms.assetid: fc52007f-c26f-4f8e-b9d8-55a7978f4d56
caps.latest.revision: 15
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 15
---
# Configurar un Firewall para el acceso de FILESTREAM
  Para utilizar FILESTREAM en un entorno protegido mediante firewall, tanto el cliente como el servidor deben poder resolver los nombres DNS en el servidor que contenga los archivos FILESTREAM. FILESTREAM requiere que los puertos 139 y 445 de uso compartido de archivos de Windows estén abiertos.  
  
### Para abrir los puertos de uso compartido de archivos de Windows en un equipo que ejecuta Windows 7  
  
1.  En el Panel de control, abra **Firewall de Windows**.  
  
2.  En el panel izquierdo, haga clic en **Configuración avanzada**. Si le solicitan una contraseña de administrador o le piden confirmación, escriba la contraseña o proporcione la confirmación.  
  
3.  En el cuadro de diálogo **Firewall de Windows con seguridad avanzada** , en el panel izquierdo, haga clic en **Reglas de entrada**y, a continuación, en el panel derecho, haga clic en **Nueva regla**.  
  
4.  Siga las instrucciones del Asistente para nueva regla de entrada para agregar el puerto TCP 139.  
  
5.  Repita el paso anterior para agregar el puerto TCP 445.  
  
6.  Cierre el cuadro de diálogo de **Firewall de Windows con seguridad avanzada** .  
  
  