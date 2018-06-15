---
title: Tipos definidos por el usuario CLR grandes (OLE DB) | Documentos de Microsoft
description: Tipos definidos por el usuario de CLR grandes (OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: ac07bf034e65d654a2b8577bdad8d5f3fb8ff48d
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2018
ms.locfileid: "35611990"
---
# <a name="large-clr-user-defined-types-ole-db"></a>Tipos definidos por el usuario de CLR grandes (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Este tema describen los cambios realizados en OLE DB en el controlador OLE DB para SQL Server para admitir grandes tipos common language runtime (CLR) definido por el usuario (UDT).  
  
 Para obtener más información sobre la compatibilidad con UDT CLR grandes en el controlador de OLE DB para SQL Server, vea [Large CLR User-Defined tipos](../../oledb/features/large-clr-user-defined-types.md). Para obtener un ejemplo, vea [UDT de CLR grandes de uso &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-large-clr-udts-ole-db.md).  
  
## <a name="data-format"></a>Formato de datos  
 Controlador de OLE DB para SQL Server utiliza ~ 0 para representar la longitud de los valores que tienen un tamaño ilimitado para tipos de objetos grandes (LOB). ~0 también representa el tamaño de UDT CLR superiores a 8.000 bytes.  
  
 En la tabla siguiente se muestra la asignación de tipos de datos en parámetros y conjuntos de filas:  
  
|Tipo de datos de SQL Server|Tipo de datos de OLE DB|Diseño de memoria|Valor|  
|--------------------------|----------------------|-------------------|-----------|  
|UDT CLR|DBTYPE_UDT|BYTE [] (matriz de bytes\)|132 (oledb.h)|  
  
 Los valores UDT se representan como matrices de bytes. Se admiten conversiones a cadenas hexadecimales y desde cadenas hexadecimales. Los valores literales se representan como cadenas hexadecimales con el prefijo "0x". Una cadena hexadecimal es la representación textual de datos binarios en base 16. Un ejemplo es una conversión de tipo de servidor **varbinary(10)** a DBTYPE_STR, que da como resultado en su representación hexadecimal de 20 caracteres donde cada par de caracteres representa un solo byte.  
  
## <a name="parameter-properties"></a>Propiedades de parámetro  
 El conjunto de propiedades DBPROPSET_SQLSERVERPARAMETER admite UDT a través de OLE DB. Para obtener más información, consulte [Defined Types](../../oledb/features/using-user-defined-types.md).  
  
## <a name="column-properties"></a>Propiedades de columna  
 El conjunto de propiedades DBPROPSET_SQLSERVERCOLUMN admite la creación de tablas a través de OLE DB. Para obtener más información, consulte [Defined Types](../../oledb/features/using-user-defined-types.md).  
  
## <a name="data-type-mapping-in-itabledefinitioncreatetable"></a>Asignar tipo de datos en ITableDefinition::CreateTable  
 La siguiente información se usa en **DBCOLUMNDESC** estructuras utilizadas por ITableDefinition:: CreateTable cuando se requieren columnas UDT:  
  
|Tipo de datos OLE DB (*wType*)|*pwszTypeName*|Tipo de datos de SQL Server|*rgPropertySets*|  
|----------------------------------|--------------------|--------------------------|----------------------|  
|DBTYPE_UDT|Pasa por alto|UDT|Debe incluir un conjunto de propiedades DBPROPSET_SQLSERVERCOLUMN.|  
  
## <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 Devuelve información de la estructura DBPARAMINFO a través de **prgParamInfo** es como sigue:  
  
|Tipo de parámetro|*wType*|*ulParamSize*|*bPrecision*|*bScale*|*dwFlags* DBPARAMFLAGS_ISLONG|  
|--------------------|-------------|-------------------|------------------|--------------|------------------------------------|  
|DBTYPE_UDT<br /><br /> (longitud menor o igual a 8.000 bytes)|"DBTYPE_UDT"|*n*|no definido|no definido|clear|  
|DBTYPE_UDT<br /><br /> (longitud mayor que 8.000 bytes)|"DBTYPE_UDT"|~0|no definido|no definido|conjunto|  
  
## <a name="icommandwithparameterssetparameterinfo"></a>ICommandWithParameters::SetParameterInfo  
 La información que se proporciona en la estructura DBPARAMBINDINFO debe cumplir lo siguiente:  
  
|Tipo de parámetro|*pwszDataSourceType*|*ulParamSize*|*bPrecision*|*bScale*|*dwFlags* DBPARAMFLAGS_ISLONG|  
|--------------------|--------------------------|-------------------|------------------|--------------|------------------------------------|  
|DBTYPE_UDT<br /><br /> (longitud menor o igual a 8.000 bytes)|DBTYPE_UDT|*n*|no se tiene en cuenta|no se tiene en cuenta|Debe establecerse si el parámetro va a pasarse utilizando DBTYPE_IUNKNOWN.|  
|DBTYPE_UDT<br /><br /> (longitud mayor que 8.000 bytes)|DBTYPE_UDT|~0|no se tiene en cuenta|no se tiene en cuenta|no se tiene en cuenta|  
  
## <a name="isscommandwithparameters"></a>ISSCommandWithParameters  
 Las aplicaciones utilizan **ISSCommandWithParameters** para obtener y establecer las propiedades de parámetro definidas en la sección de propiedades de los parámetros.  
  
## <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 Éstas son las columnas que se devuelven:  
  
|Tipo de columna|DBCOLUMN_TYPE|DBCOLUMN_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE|DBCOLUMN_FLAGS_ISLONG|DBCOLUMNS_ISSEARCHABLE|DBCOLUMN_OCTETLENGTH|  
|-----------------|--------------------|--------------------------|-------------------------|---------------------|-----------------------------|-----------------------------|---------------------------|  
|DBTYPE_UDT<br /><br /> (longitud menor o igual a 8.000 bytes)|DBTYPE_UDT|*n*|NULL|NULL|Desactivar|DB_ALL_EXCEPT_LIKE|n|  
|DBTYPE_UDT<br /><br /> (longitud mayor que 8.000 bytes)|DBTYPE_UDT|~0|NULL|NULL|Establecer|DB_ALL_EXCEPT_LIKE|0|  
  
 También se definen las columnas siguientes para los UDT:  
  
|Identificador de columna|Tipo|Descripción|  
|-----------------------|----------|-----------------|  
|DBCOLUMN_UDT_CATALOGNAME|DBTYPE_WSTR|Para las columnas UDT, nombre del catálogo donde se define el UDT.|  
|DBCOLUMN_UDT_SCHEMANAME|DBTYPE_WSTR|Para las columnas UDT, nombre del esquema donde se define el UDT.|  
|DBCOLUMN_UDT_NAME|DBTYPE_WSTR|Para las columnas UDT, nombre de una sola parte del UDT.|  
|DBCOLUMN_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Para las columnas UDT, nombre de tipo completo del UDT. El nombre completo del tipo de ensamblado permite crear instancias de un objeto de ese tipo con el método Type.GetType.|  
  
## <a name="icolumnsinfogetcolumninfo"></a>IColumnsInfo::GetColumnInfo  
 La información que se devuelve en la estructura DBCOLUMNINFO es la siguiente:  
  
|Tipo de parámetro|*wType*|*ulColumnSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBCOLUMNFLAGS_ISLONG|  
|--------------------|-------------|--------------------|------------------|--------------|-----------------------------------------|  
|DBTYPE_UDT<br /><br /> (longitud menor o igual a 8.000 bytes)|DBTYPE_UDT|*n*|~0|~0|Desactivar|  
|DBTYPE_UDT<br /><br /> (longitud mayor que 8.000 bytes)|DBTYPE_UDT|~0|~0|~0|Establecer|  
  
## <a name="columns-rowset-schema-rowsets"></a>Conjunto de filas COLUMNS (conjuntos de filas de esquema)  
 Para los tipos UDT se devuelven los siguientes valores de columna:  
  
|Tipo de columna|DATA_TYPE|COLUMN_FLAGS, DBCOLUMFLAGS_ISLONG|CHARACTER_OCTET_LENGTH|  
|-----------------|----------------|-----------------------------------------|------------------------------|  
|DBTYPE_UDT<br /><br /> (longitud menor o igual a 8.000 bytes)|DBTYPE_UDT|Desactivar|*n*|  
|DBTYPE_UDT<br /><br /> (longitud mayor que 8.000 bytes)|DBTYPE_UDT|Establecer|0|  
  
 También se definen las siguientes columnas adicionales para los UDT:  
  
|Identificador de la columna|Tipo|Descripción|  
|-----------------------|----------|-----------------|  
|SS_UDT_CATALOGNAME|DBTYPE_WSTR|Para las columnas UDT, nombre del catálogo donde se define el UDT.|  
|SS_UDT_SCHEMANAME|DBTYPE_WSTR|Para las columnas UDT, nombre del esquema donde se define el UDT.|  
|SS_UDT_NAME|DBTYPE_WSTR|Para las columnas UDT, nombre de una sola parte del UDT.|  
|SS_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Para las columnas UDT, se trata del nombre de tipo completo del UDT. El nombre completo del tipo de ensamblado permite crear instancias de un objeto de ese tipo con el método Type.GetType.|  
  
 Con respecto al conjunto de filas PROCEDURE_PARAMETERS, DATA_TYPE contiene los mismos valores que el conjunto de filas de esquema COLUMNS, y TYPE_NAME contiene UDT. También se definen las mismas columnas adicionales.  
  
 Los tipos definidos por el usuario no aparecerán en el conjunto de filas de esquema PROVIDER_TYPES.  
  
## <a name="bindings-and-conversions"></a>Enlaces y conversiones  
  
|Tipo de datos de enlace|UDT a servidor|No UDT a servidor|UDT desde servidor|No UDT desde servidor|  
|----------------------|-------------------|------------------------|---------------------|--------------------------|  
|DBTYPE_UDT|Compatible (5)|Error (1)|Compatible (5)|Error (4)|  
|DBTYPE_BYTES|Compatible (5)|N/D|Compatible (5)|N/D|  
|DBTYPE_WSTR|Compatible (2), (5)|N/D|Compatible (3), (5), (6)|N/D|  
|DBTYPE_BSTR|Compatible (2), (5)|N/D|Compatible (3), (5)|N/D|  
|DBTYPE_STR|Compatible (2), (5)|N/D|Compatible (3), (5)|N/D|  
|DBTYPE_IUNKNOWN|Compatible (6)|N/D|Compatible (6)|N/D|  
|DBTYPE_VARIANT (VT_UI1 &AMP;#124; VT_ARRAY)|Compatible (5)|N/D|Compatible (3), (5)|N/D|  
|DBTYPE_VARIANT (VT_BSTR)|Compatible (2), (5)|N/D|N/D|N/D|  
  
### <a name="key-to-symbols"></a>Clave de los símbolos  
  
|Símbolo|Significado|  
|------------|-------------|  
|1|Si un servidor de tipo distinto de DBTYPE_UDT se especifica con **ICommandWithParameters:: SetParameterInfo** y el tipo de descriptor de acceso es DBTYPE_UDT, se produce un error cuando se ejecuta la instrucción.  El error será DB_E_ERRORSOCCURRED y el estado del parámetro será DBSTATUS_E_BADACCESSOR.<br /><br /> Es un error especificar un parámetro de tipo UDT en un parámetro de servidor que no es un UDT.|  
|2|Los datos se convierten de una cadena hexadecimal a datos binarios.|  
|3|Los datos se convierten de datos binarios a una cadena hexadecimal.|  
|4|Puede producirse una validación cuando se usa **CreateAccessor** o **GetNextRows**. El error es DB_E_ERRORSOCCURRED. El estado del enlace se establece en DBBINDSTATUS_UNSUPPORTEDCONVERSION.|  
|5|Puede utilizarse BY_REF.|  
|6|Los parámetros UDT pueden enlazarse como DBTYPE_IUNKNOWN en DBBINDING. Enlace a DBTYPE_IUNKNOWN indica que la aplicación desea procesar los datos como una secuencia mediante la interfaz ISequentialStream. Cuando un consumidor especifica *wType* en un enlace como un tipo DBTYPE_IUNKNOWN y la columna correspondiente o la salida parámetro del procedimiento almacenado es un UDT, el controlador OLE DB para SQL Server devolverá ISequentialStream. Para un parámetro de entrada, controlador de OLE DB para SQL Server realizará una consulta para el de la interfaz ISequentialStream.<br /><br /> En el caso de UDT grandes, puede decidir no enlazar la longitud de los datos UDT mientras utiliza el enlace DBTYPE_IUNKNOWN. Sin embargo, la longitud debe enlazarse en los UDT pequeños. Un parámetro DBTYPE_UDT puede especificarse como un UDT grande si se cumplen una o varias de las siguientes condiciones:<br />*ulParamParamSize* es ~ 0.<br />DBPARAMFLAGS_ISLONG está establecido en la estructura DBPARAMBINDINFO.<br /><br /> Para los datos de fila, el enlace DBTYPE_IUNKNOWN solamente se permite en los UDT grandes. Puede averiguar si una columna es un tipo UDT grande mediante el método IColumnsInfo:: GetColumnInfo en un conjunto de filas o IColumnsInfo, interfaz del objeto de comando. Una columna DBTYPE_UDT es una columna UDT grande si se cumplen una o varias de las siguientes condiciones:<br />Marca DBCOLUMNFLAGS_ISLONG está establecida en *dwFlags* miembro de la estructura DBCOLUMNINFO. <br />*ulColumnSize* miembro de DBCOLUMNINFO es ~ 0.|  
  
 DBTYPE_NULL y DBTYPE_EMPTY pueden enlazarse en parámetros de entrada, pero no en parámetros de salida ni en resultados. Cuando se enlazan en parámetros de entrada, el estado debe establecerse en DBSTATUS_S_ISNULL para DBTYPE_NULL o DBSTATUS_S_DEFAULT para DBTYPE_EMPTY. DBTYPE_BYREF no puede utilizarse con DBTYPE_NULL ni con DBTYPE_EMPTY.  
  
 DBTYPE_UDT también puede convertirse a DBTYPE_EMPTY y DBTYPE_NULL. Sin embargo, DBTYPE_NULL y DBTYPE_EMPTY no pueden convertirse a DBTYPE_UDT. Este comportamiento es coherente con el de DBTYPE_BYTES. **ISSCommandWithParameters** se utiliza para procesar UDT como parámetros.  
  
 Conversiones de datos proporcionadas por servicios principales de OLE DB (**IDataConvert**) no son aplicables a DBTYPE_UDT.  
  
 No se admite ningún otro enlace.  
  
## <a name="comparability-for-irowsetfind"></a>Comparaciones en IRowsetFind  
 En los tipos UDT, solo se admiten las siguientes comparaciones:  
  
-   EQ  
  
-   NE  
  
-   IGNORE  
  
 Si se intenta realizar cualquier otra comparación, se devuelve DB_E_BADCOMPAREOP.  
  
## <a name="bcp-support-for-udts"></a>Compatibilidad de BCP con los UDT  
 Valores UDT se pueden importar y exportar solo como valores de caracteres o binarios.  
  
## <a name="down-level-client-behavior-for-udts"></a>Comportamiento de cliente de nivel inferior para los UDT  
 Los UDT están sujetos a la asignación de tipos con clientes de nivel inferior, tal y como se indica a continuación:  
  
|Versión del cliente|DBTYPE_UDT<br /><br /> (longitud menor o igual a 8.000 bytes)|DBTYPE_UDT<br /><br /> (longitud mayor que 8.000 bytes)|  
|--------------------|------------------------------------------------------------------|---------------------------------------------------------|  
|SQL Server 2005|UDT|varbinary(max)|  
|SQL Server 2008 y posterior|UDT|UDT|  
  
 Cuando **DataTypeCompatibility** (SSPROP_INIT_DATATYPECOMPATIBILITY) se establece en "80", los tipos UDT grandes se muestran a los clientes de la misma manera que aparecen para los clientes de nivel inferior.  
  
## <a name="see-also"></a>Vea también  
 [Tipos definidos por el usuario de CLR grandes](../../oledb/features/large-clr-user-defined-types.md)  
  
  

