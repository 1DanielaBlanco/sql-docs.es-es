---
title: Las condiciones de memoria insuficiente y las grandes colecciones de esquemas XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- out-of-memory conditions
- XML schema collections [SQL Server], large
ms.assetid: 29b9d839-aaaf-48fb-be17-840c751f36f1
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 224ec2569dd63acf41535c489211ba8f095eb8f7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48217835"
---
# <a name="large-xml-schema-collections-and-out-of-memory-conditions"></a>Las condiciones de memoria insuficiente y las grandes colecciones de esquemas XML.
  Se puede producir una condición de memoria insuficiente durante una llamada a la función XML_SCHEMA_NAMESPACE() integrada de una colección de esquemas XML de gran tamaño o cuando intenta quitar colecciones de esquemas XML de gran tamaño. A continuación, se exponen las soluciones que se pueden aplicar en estos casos:  
  
-   Cuando la carga del sistema no es muy importante, use el comando DROP_XML_SCHEMA_COLLECTION. Si no funciona correctamente, ponga la base de datos en modo de usuario único mediante la instrucción ALTER DATABASE y vuelva a probar DROP XML SCHEMA COLLECTION. Si la colección de esquemas XML existe en **master**, **model**o **tempdb**, se deberá reiniciar el servidor para el modo de usuario único.  
  
-   Cuando llame a XML_SCHEMA_NAMESPACE, puede intentar recuperar un solo espacio de nombres XML, intentar realizar la llamada cuando la carga del sistema es menos importante o realizarla en modo de usuario único.  
  
## <a name="see-also"></a>Vea también  
 [Requisitos y limitaciones de las colecciones de esquemas XML en el servidor](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
