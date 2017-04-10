---
title: "Volver a generar procedimientos transaccionales personalizados para reflejar cambios de esquema | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "procedimientos personalizados [replicación de SQL Server]"
  - "replicación transaccional, replicar cambios de esquema"
  - "esquemas [replicación de SQL Server], replicar cambios"
ms.assetid: ccf68a13-e748-4455-8168-90e6d2868098
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Volver a generar procedimientos transaccionales personalizados para reflejar cambios de esquema
  De manera predeterminada, la replicación transaccional lleva a cabo todos los cambios de datos en los suscriptores a través de procedimientos almacenados generados por procedimientos internos para cada artículo de la tabla en la publicación. Los tres procedimientos (para inserciones, actualizaciones y eliminaciones, respectivamente) se copian al suscriptor y se ejecutan cuando se replica una inserción, actualización o eliminación en el suscriptor. Cuando se realiza un cambio de esquema en una tabla de un publicador de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], la replicación vuelve a generar automáticamente estos procedimientos, llamando al mismo conjunto de procedimientos internos de scripting para que los nuevos procedimientos coincidan con el nuevo esquema (no se admite la replicación de cambios de esquema para los publicadores de Oracle).  
  
 También es posible especificar procedimientos personalizados para reemplazar uno o más de los procedimientos predeterminados. Los procedimientos personalizados se deben modificar si el cambio de esquema va a afectar al procedimiento. Por ejemplo, si un procedimiento hace referencia a una columna que se quita en un cambio de esquema, se deben quitar del procedimiento las referencias a esa columna. La replicación propaga un nuevo procedimiento personalizado a los suscriptores de dos maneras:  
  
-   La primera opción es utilizar un procedimiento de scripting personalizado para reemplazar los valores predeterminados que utiliza la replicación:  
  
    1.  Al ejecutar [sp_addarticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md), garantizar la **@schema_option** es bit 0 x 02 **true**.  
  
    2.  Ejecutar [sp_register_custom_scripting & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md) y especifique un valor de 'insert', 'update' o 'delete' para el parámetro **@type** y procedimiento para el parámetro de secuencias de comandos el nombre de la clase **@value**.  
  
     La siguiente vez que se lleve a cabo un cambio de esquema, la replicación llamará a este procedimiento almacenado para crear un script de la definición para el nuevo procedimiento almacenado personalizado definido por el usuario y, después, propagará el procedimiento a cada suscriptor.  
  
-   La segunda opción es utilizar un script que contenga una nueva definición de procedimiento personalizado:  
  
    1.  Al ejecutar [sp_addarticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md), establezca el **@schema_option** bit 0 x 02 **false** por lo que la replicación no generan automáticamente procedimientos personalizados en el suscriptor.  
  
    2.  Antes de cada cambio de esquema, cree un nuevo archivo de secuencia de comandos y registrar el script con la replicación mediante la ejecución de [sp_register_custom_scripting & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md). Especifique un valor de 'custom_script' para el parámetro **@type** y la ruta de acceso al script en el publicador para el parámetro **@value**.  
  
     La siguiente vez que realice un cambio de esquema importante, este script se ejecutará en cada suscriptor en la misma transacción que el comando DDL. Una vez realizado el cambio de esquema, el script se elimina del registro. Debe volver a registrar el script para que se ejecute de nuevo después del siguiente cambio de esquema.  
  
## Vea también  
 [Especificar cómo se propagan los cambios para los artículos transaccionales](../../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md)   
 [Realizar cambios de esquema en bases de datos de publicaciones](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  