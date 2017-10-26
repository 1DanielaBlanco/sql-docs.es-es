---
title: Propiedades personalizadas del origen ODBC | Documentos de Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 362bbcd8-b7b0-4bab-8afe-1212b2ad1af9
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 15c78bdb8f093b07ce62a7d710ba583aad96548d
ms.contentlocale: es-es
ms.lasthandoff: 08/03/2017

---
# <a name="odbc-source-custom-properties"></a>Propiedades personalizadas del origen ODBC
  En la tabla siguiente se describen las propiedades personalizadas del origen ODBC. Todas las propiedades se pueden establecer a partir de expresiones SSIS.  
  
|Nombre de la propiedad|Tipo de datos|Description|  
|-------------------|---------------|-----------------|  
|Conexión|Conexión ODBC|Conexión ODBC para acceder a la base de datos de origen.|  
|AccessMode|Integer (enumeración)|Modo que se usa para tener acceso a la base de datos. Los valores posibles son Nombre de tabla (0) y Comando SQL (1).<br /><br /> Nombre de tabla (0) es el valor predeterminado.|  
|BatchSize|Integer|Tamaño de lote para la extracción masiva. Es el número de registros extraídos como matriz. Si el proveedor ODBC seleccionado no admite matrices, el tamaño de lote es 1.|  
|BindCharColumnAs|Integer (enumeración)|Esta propiedad determina cómo el origen ODBC enlaza las columnas con tipos string de varios bytes como SQL_CHAR, SQL_VARCHAR o SQL_LONGVARCHAR.<br /><br /> Los valores posibles son Unicode (0), que enlaza las columnas como SQL_C_WCHAR, y ANSI (1), que enlaza las columnas como SQL_C_CHAR). El valor predeterminado es Unicode (0).<br /><br /> **Nota**: la propiedad no está disponible en el **Editor de origen de ODBC**, pero se puede establecer con el **Editor avanzado**.|  
|BindNumericAs|Integer (enumeración)|Esta propiedad determina el modo en que el origen ODBC enlaza columnas con datos numéricos con los tipos de datos SQL_TYPE_NUMERIC y SQL_TYPE_DECIMAL.<br /><br /> Las opciones posibles son Char (0), que enlaza las columnas como SQL_C_CHAR y Numeric (1), que enlaza las columnas como SQL_C_NUMERIC. El valor predeterminado es Char (0).<br /><br /> **Nota**: la propiedad no está disponible en el **Editor de origen de ODBC**, pero se puede establecer con el **Editor avanzado**.|  
|DefaultCodePage|Integer|Página de códigos que se usará para las columnas de salida.<br /><br /> **Nota**: la propiedad no está disponible en el **Editor de origen de ODBC**, pero se puede establecer con el **Editor avanzado**.|  
|ExposeCharColumnsAsUnicode|Boolean|Esta propiedad determina el modo en que el componente expone las columnas CHAR. El valor predeterminado es False, que indica que las columnas CHAR se exponen como cadenas de varios bytes (DT_STR). Si es True, las columnas CHAR se exponen como cadenas anchas (DT_WSTR).<br /><br /> **Nota**: la propiedad no está disponible en el **Editor de origen de ODBC**, pero se puede establecer con el **Editor avanzado**.|  
|FetchMethod|Integer (enumeración)|Método usado para obtener los datos. Las opciones posibles son fila por fila (0) y lote (1). El valor predeterminado es lote (1).<br /><br /> Para obtener más información acerca de estas opciones, consulte [ODBC Source](../../integration-services/data-flow/odbc-source.md).<br /><br /> **Nota**: la propiedad no está disponible en el **Editor de origen de ODBC**, pero se puede establecer con el **Editor avanzado**.|  
|SqlCommand|String|Comando SQL que se va a ejecutar cuando AccessMode se establece en SQL Command.|  
|StatementTimeout|Integer|Número de segundos que se esperará a que una instrucción SQL se ejecute antes de volver, con un error, a la aplicación. El valor predeterminado es 120. El valor 0 indica que el sistema no agota el tiempo de espera.|  
|TableName|String|Nombre de la tabla con los datos que se usan cuando AccessMode se establece en el nombre de tabla.|  
|LobChunckSize|Integer|Asignación de tamaño del fragmento para las columnas LOB.|  
||||  
  
## <a name="see-also"></a>Vea también  
 [Origen de ODBC](../../integration-services/data-flow/odbc-source.md)   
 [Editor de origen ODBC &#40; Página Administrador de conexiones &#41;](../../integration-services/data-flow/odbc-source-editor-connection-manager-page.md)  
  
  

