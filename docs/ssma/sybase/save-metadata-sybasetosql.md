---
title: Guardar metadatos (SybaseToSQL) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: b2517735-dd19-449f-8cee-08e68ca89d3a
caps.latest.revision: 3
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 5cb17fa5dcec7a01f1067db8b09604ea69dc9411
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34779521"
---
# <a name="save-metadata--sybasetosql"></a>Guardar metadatos (SybaseToSQL)
El **guardar metadatos** cuadro de diálogo le pregunta si desea cargar los metadatos en el proyecto SSMA antes de guardarla. Esto permite tener un archivo de proyecto completo que se puede utilizar sin conexión y enviar a otras personas, como el personal de soporte técnico.  
  
Para tener acceso a la **guardar metadatos** cuadro de diálogo, guarde el proyecto. Si los metadatos no están presente, SSMA mostrará el **guardar metadatos** cuadro de diálogo.  
  
## <a name="options"></a>Opciones  
**Nombre**  
El nombre de cada base de datos en el proyecto.  
  
**Estado**  
Indica si los metadatos se cargan en el proyecto SSMA, o si hay metadatos que faltan.  
  
SSMA carga los metadatos en el proyecto según sea necesario. Metadatos se cargan automáticamente al examinar los metadatos y convertir esquemas.  
  
**Seleccionar todo**  
Selecciona todas las bases de datos.  
  
**Desactivar**  
Borra la casilla de verificación para todas las bases de datos que le faltan metadatos. No puede desactivar la casilla de verificación si se ha cargado un metadatos.  
  
**Guardar**  
Guarda el proyecto, cargar los metadatos de las bases de datos seleccionado que les faltan metadatos.  
  
**Cancelar**  
Cancela la operación de guardar operación. Metadatos que faltan no se cargan en el proyecto.  
  
