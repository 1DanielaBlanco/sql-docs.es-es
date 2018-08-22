---
title: EntityType, elemento (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 372e2c13-ec38-4bb1-981c-50758d59a1da
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a7322f12605256fe25bb533c0360467510be92e2
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2018
ms.locfileid: "40392404"
---
# <a name="entitytype-element-csdlbi"></a>EntityType, elemento (CSDLBI)
  El elemento `EntityType` es un tipo complejo que representa la estructura de una entidad de nivel superior, como un cliente o un pedido, en un modelo de datos. El `bi:EntityType` elemento extiende la definición de [EntityType](http://msdn.microsoft.com/library/bb399206.aspx) usado en el [Entity Data Framework](/dotnet/framework/data/adonet/ef/overview).  
  
 Se debe especificar un elemento EntityType para cada una de las entidades incluidas en el modelo de datos. Los subelementos de EntityType describen las columnas y medidas de la tabla. Las relaciones entre las tablas se incluyen en el elemento `EntityContainer`.  
  
## <a name="elements-and-attributes"></a>Atributos y elementos  
 En la tabla siguiente se enumeran los elementos y atributos que definen el elemento `EntityType`. Vea también los atributos aplicables al elemento [EntityType](http://msdn.microsoft.com/library/bb399206.aspx) .  
  
|Nombre|Es obligatorio|Descripción|  
|----------|-----------------|-----------------|  
|Contenido|no|Cadena que contiene los posibles tipos de datos de una columna. El valor se deriva del valor de DimensionAttributeTypeEnumType en el modelo de datos.<br /><br /> Si el valor de DimensionAttributeTypeEnumType es “ExtendedType”, el valor de Contents se deriva del elemento ExtendedType de DimensionAttribute. No es necesario que el cliente responda a estos valores.|  
|DefaultDetails|no|Lista de referencias de propiedad que representan el conjunto de columnas de la tabla.<br /><br /> Consulte [elemento DefaultDetails &#40;CSDLBI&#41;](defaultdetails-element-csdlbi.md).|  
|DefaultImage|no|Referencia a una columna que contiene la imagen que ilustra la entidad.<br /><br /> En los modelos multidimensionales, este elemento corresponde a un atributo binario en el atributo de dimensión. Si este atributo está presente, el elemento debe contener exactamente un elemento MemberRef.<br /><br /> Consulte [elemento MemberRef &#40;CSDLBI&#41;](memberref-element-csdlbi.md).|  
|DefaultMeasure|no|Referencia a una medida de la entidad que se debe utilizar como valor predeterminado al realizar cálculos en dicha entidad. Si no se especifica, el valor predeterminado es SUM.<br /><br /> Consulte [elemento MemberRef &#40;CSDLBI&#41;](memberref-element-csdlbi.md).|  
|DisplayKey|no|Lista de referencias a columnas o a extremos de rol que constituye un identificador seguro que identifica de forma exclusiva una instancia de entidad.<br /><br /> Consulte [elemento DisplayKey &#40;CSDLBI&#41;](displaykey-element-csdlbi.md).|  
|Hierarchy|no|Lista de jerarquías del modelo.<br /><br /> Consulte [Hierarchy, elemento &#40;CSDLBI&#41;](hierarchy-element-csdlbi.md).|  
|ReferenceName|Sí|Identificador que se puede utilizar para hacer referencia a esta entidad en una consulta de expresiones de análisis de datos (DAX).<br /><br /> Si este atributo no está presente, se utiliza el nombre de campo completo de la entidad.|  
|SortMembers|no|Lista de propiedades según las que se ordena. El atributo SortDirection indica si el orden es ascendente o descendente.|  
  
## <a name="contents-element"></a>Elemento Contents  
 El elemento `Contents` es un tipo simple que describe el tipo de datos de la entidad.  
  
 El contenido de la entidad (columna) pueden ser cualquiera de los valores siguientes:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|Regular|No se define de otro modo.|  
|Time|Los atributos representan periodos de tiempo, como años, semestres, trimestres, meses o días.|  
|Geografía|Los atributos representan información geográfica, como ciudades o códigos postales.|  
|Organización|Los atributos representan información organizativa, como empleados o subsidiarias.|  
|Lista de materiales|Los atributos representan información de inventario o de fabricación, como listas de piezas para productos.|  
|Cuentas|Los atributos representan un gráfico de cuentas para informes financieros.|  
|Clientes|Los atributos representan información de clientes o de contacto.|  
|Productos|Los atributos representan información de productos.|  
|Escenario|Los atributos representan información de planeación o análisis estratégico.|  
|Cuantitativa|Los atributos representan información cuantitativa.|  
|Utilidad|Los atributos representan información diversa.|  
|Moneda|Contiene datos y metadatos de moneda.|  
|Tarifas|Los atributos representan información de tasa de cambio.|  
|Canal|Los atributos representan información de canal.|  
|Promoción|Los atributos representan información de promociones de marketing.|  
  
## <a name="example"></a>Ejemplo  
 **Tabular**  
  
 En el ejemplo siguiente se muestra parte de la representación de la versión 1.1 de CSDLBI de la tabla Geography utilizada en el modelo tabular AdventureWorks. La columna RowNumber es una columna oculta generada automáticamente como identificador de fila en los modelos tabulares, por lo que tiene el atributo Contents, `RowNumber`.  
  
```  
  
<EntityType   
     Name="DimGeography">  
     <Key>  
        <PropertyRef Name="RowNumber" />  
     </Key>  
     <Property   
        Name="RowNumber"   
        Type="Int64" Nullable="false">  
     <bi:Property   
        Hidden="true"   
        Contents="RowNumber"   
        Stability="RowNumber" />  
     </Property>  
....  
  
```  
  
## <a name="example"></a>Ejemplo  
 **Multidimensional**  
  
 En el ejemplo siguiente se muestran los elementos EntityType de la versión 1.1 de CSDLBI que representan una parte de una dimensión de tiempo del cubo de operaciones de Contoso.  
  
```  
<EntityType   
       Name="CalendarQuarter">  
    <Key>  
       <PropertyRef Name="RowNumber" />  
    </Key>  
  
    <Property Name="RowNumber"   
       Type="Int64"   
       Nullable="false">  
    <bi:Property   
       Hidden="true"   
       Contents="RowNumber"   
       Stability="RowNumber"   
    />  
    </Property>  
  
    <Property Name="CalendarQuarter2"   
       Type="String"   
       MaxLength="Max"   
       Unicode="true"   
       FixedLength="false"   
       Nullable="false">  
    <bi:Property   
       Caption="CalendarQuarter"   
       ReferenceName="CalendarQuarter"   
    />  
    </Property>  
   <bi:EntityType />  
</EntityType>  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia técnica para las anotaciones de Business Intelligence en CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
