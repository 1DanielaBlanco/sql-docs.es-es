---
title: Consideraciones de seguridad de diagrama de actualización (SQLXML 4.0) | Documentos de Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLXML, updategrams
- security [SQLXML], updategrams
- updategrams [SQLXML], security
ms.assetid: 00dc6cf4-a2e8-4cca-bdd6-d5122102a82d
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6f9a1227be077396e9e7575780be16c7b0a9fa04
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32967940"
---
# <a name="updategram-security-considerations-sqlxml-40"></a>Consideraciones de seguridad sobre los diagramas de actualización (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  A continuación, se muestran una serie de instrucciones de seguridad para usar diagramas de actualización:  
  
-   Evite el uso de la asignación predeterminada cuando utilice los diagramas de actualización para actualizar datos. Cuando se utiliza la asignación predeterminada, un nombre de elemento de un diagrama de actualización se asigna a un nombre de tabla y un nombre de atributo se asigna a una columna. De esta forma, la información de la columna y la tabla de base de datos se expone en la base de datos, lo que puede suponer un riesgo potencial para la seguridad. En lugar de ello, si especifica un esquema de asignación independiente que asigne los elementos y atributos de un diagrama de actualización a las columnas y las tablas de base de datos, los nombres de los atributos y los elementos del diagrama de actualización pueden ser arbitrarios y el esquema realiza la asignación necesaria de estos nombres a las columnas y las tablas de base de datos. Así, la información de la base de datos no se expone en un diagrama de actualización.  
  
-   No permita que los usuarios creen y ejecuten sus diagramas de actualización. Es recomendable que los diagramas de actualización residan como plantillas en un servidor en lugar de crearlos dinámicamente en aplicaciones de tipo ASP, lo que podría poner en peligro los datos de la base de datos. Permitir que los usuarios obtengan acceso a los datos solamente a través de los diagramas de actualización, suministrados como plantillas, puede eliminar este riesgo.  
  
## <a name="see-also"></a>Vea también  
 [Usar diagramas de actualización para modificar datos en SQLXML 4.0](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/using-updategrams-to-modify-data-in-sqlxml-4-0.md)  
  
  
