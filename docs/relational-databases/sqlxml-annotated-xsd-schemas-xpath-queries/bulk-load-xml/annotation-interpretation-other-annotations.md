---
title: Otras anotaciones (SQLXML 4.0) | Documentos de Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- url-encode annotation
- sql:key-fields
- use-cdata annotation
- sql:is-mapping-schema
- sql:url-encode
- sql:id-prefix
- sql:use-cdata
- key-fields annotation
- id-prefix annotation [SQLXML]
- is-mapping-schema annotation
ms.assetid: f7b4d37b-d6d3-4ac3-b2fd-a0b534a924e4
caps.latest.revision: "20"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7c66f2bb5bb89e2d8ac46fb8e6d20a8c79a49b27
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="annotation-interpretation---other-annotations"></a>Interpretación de anotaciones - otras anotaciones
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Además de las anotaciones descritas en los temas anteriores de esta sección, carga masiva XML interpreta estas otras anotaciones, como se indica a continuación:  
  
 **SQL: ID-prefijo**  
 Si el esquema especifica prefijos para los datos XML, la carga masiva de XML quita los prefijos antes de enviar los datos a Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **SQL: use-cdata**  
 La carga masiva de XML lee el texto que está almacenado en las secciones CDATA y lo envía a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **SQL-codificar**  
 La carga masiva de XML no admite esta anotación. Por ejemplo, no puede especificar una dirección URL en la entrada de datos XML y esperar que la carga masiva de XML lea los datos de esa ubicación para almacenarlos en la base de datos.  
  
 **SQL: is-mapping-schema**  
 La carga masiva de XML no admite esta anotación, ni tampoco admite **sql:id**.  
  
> [!NOTE]  
>  La carga masiva de XML no admite los esquemas de asignación insertados.  
  
 **SQL: Key-campos**  
 La carga masiva de XML omite siempre esta anotación.  
  
## <a name="see-also"></a>Vea también  
 [Interpretación de anotaciones &#40; SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sqlxml-4-0.md)  
  
  
