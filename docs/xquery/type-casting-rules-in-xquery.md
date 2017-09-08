---
title: "Tipo de reglas de conversión en XQuery | Documentos de Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- XQuery, type casting
- casting rules [XML in SQL Server]
- explicit casting [SQL Server]
- type casting rules [XML in SQL Server]
- cast as operator
- implicit casting
ms.assetid: f2e91306-2b1b-4e1c-b6d8-a34fb9980057
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b3fc531210c575742ab4af7670bb122bb7473ca3
ms.contentlocale: es-es
ms.lasthandoff: 09/01/2017

---
# <a name="type-casting-rules-in-xquery"></a>Reglas de conversión de tipos en XQuery
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  El siguiente diagrama de especificaciones de operadores y funciones de W3C XQuery 1.0 y XPath 2.0 muestra los tipos de datos integrados. Se incluyen los tipos primitivo integrado y derivado integrado.  
  
 ![Jerarquía de tipos de XQuery 1.0](../xquery/media/xquery-typing-rules.gif "jerarquía de tipos de XQuery 1.0")  
  
 Este tema describe las reglas de conversión de tipos que se aplican al realizar conversiones de un tipo a otro utilizando uno de los métodos siguientes:  
  
-   Conversión explícita que realiza mediante **convertidos en** o las funciones de constructor de tipo (por ejemplo, `xs:integer("5")`).  
  
-   Conversión implícita que se produce durante la promoción de tipo.  
  
## <a name="explicit-casting"></a>Conversión explícita  
 La tabla siguiente describe la conversión de tipo admitida entre los tipos primitivos integrados.  
  
 ![Describe las reglas de conversión de XQuery. ] (../xquery/media/casting-builtin-types.gif "Describe las reglas de conversión de XQuery.")  
  
-   Un tipo primitivo integrado puede convertirse a otro tipo primitivo integrado, en función de las reglas de la tabla.  
  
-   Un tipo primitivo puede convertirse a cualquier tipo derivado de dicho tipo primitivo. Por ejemplo, es posible convertir **xs: decimal** a **xs: Integer**, o de **xs: decimal** a **xs**.  
  
-   Un tipo derivado puede convertirse a cualquier tipo que sea su antecesor en la jerarquía de tipos, hasta llegar al tipo base primitivo integrado. Por ejemplo, es posible convertir **xs: token** a **xs: normalizedString** o a **xs: String**.  
  
-   Un tipo derivado puede convertirse a un tipo primitivo si su antecesor primitivo se puede convertir al tipo de destino. Por ejemplo, puede convertir **xs: Integer**, un tipo derivado, a un **xs: String**, primitivos de tipo, porque **xs: decimal**, **xs: Integer**del antecesor primitivo, se puede convertir en **xs: String**.  
  
-   Un tipo derivado puede convertirse a otro tipo derivado si el antecesor primitivo del tipo de origen puede convertirse al antecesor primitivo del tipo de destino. Por ejemplo, es posible convertir **xs: Integer** a **xs: token**, porque es posible convertir **xs: decimal** a **xs: String**.  
  
-   Las reglas para convertir tipos definidos por el usuario a tipos integrados son las mismas que se aplican a los tipos integrados. Por ejemplo, puede definir un **myInteger** tipo derivado de **xs: Integer** tipo. A continuación, **myInteger** pueden convertirse a **xs: token**, porque **xs: decimal** pueden convertirse a **xs: String**.  
  
 No se admiten los siguientes tipos de conversión:  
  
-   Conversión a o desde tipos de lista. Esto incluye los tipos de lista definida por el usuario y tipos de lista integrados como **xs: IDREFS**, **xs: Entities**, y **xs: NMTOKENS**.  
  
-   Conversión a o desde **xs: QName** no se admite.  
  
-   **xs: Notation** y los subtipos totalmente en orden de duración, **xdt: yearmonthduration** y **xdt: daytimeduration**, no se admiten. Como resultado, no se admite la conversión a o desde estos tipos.  
  
 Los ejemplos siguientes muestran la conversión de tipo explícito.  
  
### <a name="example-a"></a>Ejemplo A  
 En el ejemplo siguiente, se consulta una variable de tipo xml. La consulta devuelve una secuencia de un valor de tipo simple escrito en forma de xs:string.  
  
```  
declare @x xml  
set @x = '<e>1</e><e>2</e>'  
select @x.query('/e[1] cast as xs:string?')  
go  
```  
  
### <a name="example-b"></a>Ejemplo B  
 En el ejemplo siguiente, se consulta una variable xml con tipo. El ejemplo crea primero una colección de esquemas XML. A continuación, utiliza la colección de esquemas XML para crear una variable xml con tipo. El esquema proporciona la información de tipo para la instancia XML asignada a la variable. A continuación, se especifican consultas para la variable.  
  
```  
create xml schema collection myCollection as N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
      <xs:element name="root">  
            <xs:complexType>  
                  <xs:sequence>  
                        <xs:element name="A" type="xs:string"/>  
                        <xs:element name="B" type="xs:string"/>  
                        <xs:element name="C" type="xs:string"/>  
                  </xs:sequence>  
            </xs:complexType>  
      </xs:element>  
</xs:schema>'  
go  
```  
  
 La consulta siguiente devuelve un error estático porque no se sabe cuántos elementos <`root`> de nivel superior hay en la instancia de documento.  
  
```  
declare @x xml(myCollection)  
set @x = '<root><A>1</A><B>2</B><C>3</C></root>  
          <root><A>4</A><B>5</B><C>6</baz></C>'  
select @x.query('/root/A cast as xs:string?')  
go  
```  
  
 Si se especifica un elemento singleton <`root`> en la expresión, la consulta se realizará correctamente. La consulta devuelve una secuencia de un valor de tipo simple escrito en forma de xs:string.  
  
```  
declare @x xml(myCollection)  
set @x = '<root><A>1</A><B>2</B><C>3</C></root>  
              <root><A>4</A><B>5</B><C>6</C></root>'  
select @x.query('/root[1]/A cast as xs:string?')  
go  
```  
  
 En el ejemplo siguiente, la variable de tipo xml incluye una palabra clave de documento que especifica la colección de esquemas XML. Esto indica que la instancia XML debe ser un documento que tenga un elemento invidual de nivel superior. Si crea dos elementos <`root`> en la instancia XML, generará error.  
  
```  
declare @x xml(document myCollection)  
set @x = '<root><A>1</A><B>2</B><C>3</C></root>  
              <root><A>4</A><B>5</B><C>6</C></root>'  
go  
```  
  
 Puede cambiar la instancia para que solo incluya un elemento de nivel superior y la consulta. De nuevo, la consulta devuelve una secuencia de un valor de tipo simple escrito en forma de xs:string.  
  
```  
declare @x xml(document myCollection)  
set @x = '<root><A>1</A><B>2</B><C>3</C></root>'  
select @x.query('/root/A cast as xs:string?')  
go  
```  
  
## <a name="implicit-casting"></a>Conversión implícita  
 La conversión implícita solo se admite para tipos numéricos y tipos atómicos sin tipo. Por ejemplo, la siguiente **min()** función devuelve el menor de los dos valores:  
  
```  
min(xs:integer("1"), xs:double("1.1"))  
```  
  
 En este ejemplo, los dos valores pasan a la expresión XQuery **min()** función son de tipos diferentes. Por lo tanto, se efectúa una conversión implícita donde **entero** tipo se promueve a **doble** y los dos **doble** se comparan valores.  
  
 La promoción de tipo descrita en este ejemplo sigue estas reglas:  
  
-   Un tipo numérico derivado integrado puede promoverse a su tipo base. Por ejemplo, **entero** puede promoverse a **decimal**.  
  
-   A **decimal** puede promoverse a **float,** y un **float** puede promoverse a **doble**.  
  
 La conversión implícita solo se admite para tipos numéricos; no se admite en los siguientes casos:  
  
-   Conversión implícita para tipos de cadena. Por ejemplo, si dos **cadena** se esperan que los tipos y el usuario pasa un **cadena** y un **token**, se produce ninguna conversión implícita y se devuelve un error.  
  
-   La conversión implícita de tipos numéricos a tipos de cadena. Por ejemplo, si pasa un valor de tipo entero a una función que espera un parámetro de tipo cadena, no se producirá la conversión implícita y se generará error.  
  
## <a name="casting-values"></a>Valores de conversión  
 Cuando se convierte de un tipo a otro, los valores reales se transforman desde el espacio del valor del tipo de origen al espacio del valor del tipo de destino. Por ejemplo, la conversión de xs:decimal a xs:double transformará el valor decimal en un valor doble.  
  
 A continuación, se incluyen algunas reglas de transformación.  
  
##### <a name="casting-a-value-from-a-string-or-untypedatomic-type"></a>Convertir un valor a partir de un tipo de cadena o untypedAtomic  
 El valor que se convierte a un tipo de cadena o untypedAtomic se transforma del mismo modo que se valida el valor en función de las reglas del tipo de destino. Se incluyen las reglas de procesamiento de espacios en blanco y patrones posibles Por ejemplo, las reglas siguientes serán satisfactorias y generarán el valor doble 1.1e0:  
  
 `xs:double("1.1")`  
  
 Cuando se convierte a tipos binarios como s:base64Binary o xs:hexBinary desde un tipo de cadena o untypedAtomic, los valores de entrada tienen que ser de codificación base64 o hexadecimal, respectivamente.  
  
##### <a name="casting-a-value-to-a-string-or-untypedatomic-type"></a>Convertir un valor a un tipo de cadena o untypedAtomic  
 La conversión al tipo de cadena o untypedAtomic transforma el valor a su representación léxica canónica de XQuery. Concretamente, esto puede suponer que un valor que se haya ajustado a un patrón determinado o a alguna otra restricción durante la entrada de datos no se represente conforme a dicha limitación.  Para informar a los usuarios acerca de esto, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] identifica los tipos que la restricción de tipo puede ser un problema al proporcionar una advertencia cuando dichos tipos se cargan en la colección de esquemas.  
  
 Cuando se convierte un valor del tipo xs:float o xs:double, o alguno de sus subtipos, al tipo de cadena o untypedAtomic, el valor se representa en forma de notación científica. Esto solo sucede cuando el valor absoluto es menor que 1.0E-6 o mayor o igual que 1.0E6, lo que significa que 0 se serializa en notación científica a 0.0E0.  
  
 Por ejemplo, `xs:string(1.11e1)` devolverá el valor de cadena `"11.1"`, mientras que `xs:string(-0.00000000002e0)` devolverá el valor de cadena `"-2.0E-11"`.  
  
 Cuando se convierten tipos binarios como s:base64Binary o xs:hexBinary al tipo de cadena o untypedAtomic, los valores binarios se representarán en forma de codificación base64 o hexadecimal, respectivamente.  
  
##### <a name="casting-a-value-to-a-numeric-type"></a>Convertir un valor a un tipo numérico  
 Al convertir un valor de un tipo numérico a otro, el valor se asignará a partir de un espacio del valor al otro sin pasar por la serialización de cadena. Si el valor no cumple la restricción de un tipo de destino, se aplicarán las reglas siguientes:  
  
-   Si el valor de origen es numérico y el tipo de destino es xs:float o un subtipo que admite valores -INF o INF, y la conversión del valor numérico da lugar a un desbordamiento, el valor se asignaría a INF si es positivo o -INF si es negativo. Si el tipo de destino no admite INF ni -INF y se produce un desbordamiento, la conversión generará error y el resultado en esta versión de SQL Server será una secuencia vacía.  
  
-   Si el valor de origen es numérico y el tipo de destino es un tipo numérico que incluye 0, -0e0 o 0e0 en el rango de valores admitidos, y la conversión del valor numérico de origen da lugar a un desbordamiento, se realizarán las siguientes asignaciones:  
  
    -   El valor se asigna a 0 para el tipo de destino decimal.  
  
    -   El valor se asigna a 0e0 cuando es un subdesbordamiento negativo.  
  
    -   El valor se asigna a 0e0 cuando es un subdesbordamiento positivo para el tipo de destino doble o flotante.  
  
     Si el tipo de destino no incluye cero en el espacio del valor, la conversión genera un error y da lugar a una secuencia vacía.  
  
     Tenga en cuenta que la conversión de un valor al tipo flotante o binario, como xs:float, xs:double o cualquier otro subtipo, podría perder precisión.  
  
## <a name="implementation-limitations"></a>Limitaciones de la implementación  
 Éstas son las limitaciones:  
  
-   No se admite el valor de tipo flotante NaN.  
  
-   Los valores convertibles están sujetos a las restricciones de implementación de tipos de destino. Por ejemplo, no se puede convertir una cadena de fecha con un año negativo a **xs: Date**. Tales conversiones darán como resultado la secuencia vacía si el valor se proporciona en tiempo de ejecución (en lugar de generar un error en tiempo de ejecución).  
  
## <a name="see-also"></a>Vea también  
 [Definir la serialización de datos XML](../relational-databases/xml/define-the-serialization-of-xml-data.md)  
  
  
