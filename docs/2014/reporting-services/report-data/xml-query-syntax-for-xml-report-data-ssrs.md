---
title: Sintaxis de consulta XML para los datos de informe XML (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- namespaces [Reporting Services]
- data processing extensions [Reporting Services], data sources
- xmldp [Reporting Services]
- XML [Reporting Services], data retrieval
ms.assetid: d203886f-faa1-4a02-88f5-dd4c217181ef
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 65eed443f671f18944ce381a011498e3ca23af4e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48102895"
---
# <a name="xml-query-syntax-for-xml-report-data-ssrs"></a>Sintaxis de consulta XML para los datos de informe XML (SSRS)
  En [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], se pueden crear conjuntos de datos para orígenes de datos XML. Después de definir un origen de datos, se crea una consulta para el conjunto de datos. Según el tipo de datos XML señalados por el origen de datos, crear la consulta de conjunto de datos mediante la inclusión de un documento XML `Query` o una ruta de acceso de elemento. Un documento XML `Query` comienza con un  **\<consulta >** etiqueta e incluye espacios de nombres y elementos XML que varían según el origen de datos. Una ruta de acceso de elemento es independiente del espacio de nombres y especifica qué nodos y atributos de nodo se utilizan de los datos XML subyacentes con una sintaxis del tipo de XPath. Para más información sobre las rutas de acceso de elemento, vea [Sintaxis de ruta de acceso de elemento para datos de informe XML &#40;SSRS&#41;](report-data-ssrs.md).  
  
 Se pueden crear orígenes de datos XML para los siguientes tipos de datos XML:  
  
-   Documentos XML a los que señala una dirección URL mediante el protocolo HTTP  
  
-   Extremos de servicios web que devuelven datos XML  
  
-   Datos XML incrustados  
  
 La forma en que se especifica un elemento XML `Query` o una ruta de acceso de elemento depende del tipo de los datos XML.  
  
 Para un documento XML, el XML `Query` es opcional. Si se incluye, puede contener un elemento XML `ElementPath`. El valor del elemento XML `ElementPath` utiliza la sintaxis de la ruta de acceso de elemento. Incluya el XML `Query` y XML `ElementPath` para procesar los espacios de nombres correctamente cuando lo requieran los datos XML desde el origen de datos.  
  
 Para un extremo de servicios web al que señala una dirección URL de cadena de conexión, el elemento XML `Query` define el método del servicio web, la acción SOAP o ambos. El proveedor de datos XML crea una solicitud de servicio web que recupera los datos XML que se utilizarán para el informe.  
  
> [!NOTE]  
>  Cuando un espacio de nombres de servicio web incluye un carácter de barra diagonal (`/)`, deben incluirse tanto el método del servicio web como la acción SOAP, de manera que la extensión de procesamiento de datos XML pueda derivar el espacio de nombres correctamente.  
  
 Para un documento XML incrustado, el XML `Query` define los datos XML incrustados para usar, incluye espacios de nombres opcionales y contiene un elemento XML `ElementPath`...  
  
## <a name="specifying-query-parameters-for-xml-data"></a>Especificar parámetros de consulta para datos XML  
 Puede especificar parámetros de consulta para documentos XML.  
  
-   Para solicitudes de dirección URL, los parámetros de consulta se incluyen como parámetros de dirección URL estándar.  
  
-   Para solicitudes de servicio web, los parámetros de consulta se pasan al método del servicio web. Para definir un parámetro de consulta, utilice la página **Parámetros** del cuadro de diálogo **Propiedades del conjunto de datos** . Para obtener más información, consulte [cuadro de diálogo de propiedades de conjunto de datos, parámetros](dataset-properties-dialog-box-parameters.md).  
  
### <a name="example"></a>Ejemplo  
 En los ejemplos de la tabla siguiente se muestra cómo se recuperan los datos desde el servicio web del servidor de informes, un documento XML y datos XML incrustados.  
  
|Origen de datos XML|Ejemplo de consulta|  
|---------------------|-------------------|  
|Datos XML de servicio Web del método ListChildren.|`<Query>`<br /><br /> `<Method Name="ListChildren" Namespace="http://schemas.microsoft.com/sqlserver/2005/06/30/reporting/reportingservices" />`<br /><br /> `</Query>`|  
|Datos XML del servicio web obtenidos a través de SoapAction.|`<Query xmlns=namespace>`<br /><br /> `<SoapAction>http://schemas/microsoft.com/sqlserver/2005/03/23/reporting/reportingservices/ListChildren</SoapAction>`<br /><br /> `</Query>`|  
|Documento XML o datos XML incrustados que usan espacios de nombres.<br /><br /> Elemento de consulta que especifica los espacios de nombres de una ruta de acceso de elemento.|`<Query xmlns:es="http://schemas.microsoft.com/StandardSchemas/ExtendedSales">`<br /><br /> `<ElementPath>/Customers/Customer/Orders/Order/es:LineItems/es:LineItem</ElementPath>`<br /><br /> `</Query>`|  
|Documento XML incrustado.|`<Query>`<br /><br /> `<XmlData>`<br /><br /> `<Customers>`<br /><br /> `<Customer ID="1">Bobby</Customer>`<br /><br /> `</Customers>`<br /><br /> `</XmlData>`<br /><br /> `<ElementPath>Customer {@}</ElementPath>`<br /><br /> `</Query>`|  
|Documento XML que usa los valores predeterminados.|*No query*.<br /><br /> La ruta de acceso de elemento se deriva del propio documento XML y es independiente del espacio de nombres.|  
  
> [!NOTE]  
>  El primer ejemplo de servicio web muestra el contenido del servidor de informes que usa el método <xref:ReportService2006.ReportingService2006.ListChildren%2A> . Para ejecutar esta consulta, es necesario crear un nuevo origen de datos y establecer la cadena de conexión en http://localhost/reportserver/reportservice2006.asmx. El <xref:ReportService2006.ReportingService2006.ListChildren%2A> método toma dos parámetros: `Item` y `Recursive`. Establecer el valor predeterminado para `Item` a `/` y `Recursive` a `1`.  
  
## <a name="specifying-namespaces"></a>Especificar espacios de nombres  
 Use el código XML `Query` elemento para especificar los espacios de nombres que se usan en los datos XML desde el origen de datos. En la siguiente consulta XML se utiliza el espacio de nombres `sales`. Los nodos de elemento XML `ElementPath` para `sales:LineItems` y `sales:LineItem` utilizan el espacio de nombres `sales`.  
  
```  
<Query xmlns:sales=  
"http://schemas.microsoft.com/StandardSchemas/ExtendedSales">  
   <SoapAction>  
      http://schemas.microsoft.com/SalesWebService/ListOrders   
   </SoapAction>  
   <ElementPath>  
      Customers/Customer/Orders/Order/sales:LineItems/sales:LineItem  
   </ElementPath>  
</Query>  
```  
  
 Para especificar el espacio de nombres del proveedor de datos para que el espacio de nombres predeterminado permanezca vacío, use `xmldp`. Esto se muestra en el ejemplo siguiente.  
  
### <a name="example"></a>Ejemplo  
 En los ejemplos siguientes se utiliza el documento XML DPNamespace.xml, que se proporciona después de la tabla a modo de ilustración. En esta tabla se muestran dos ejemplos de sintaxis de ruta de acceso de elemento XML que incluye prefijos de espacios de nombres.  
  
|Elemento de consulta XML|Campos resultantes en el conjunto de datos|  
|-----------------------|-------------------------------------|  
|\<Query/>|Valor A: http://schemas.microsoft.com/...<br /><br /> Valor B: http://schemas.microsoft.com/...<br /><br /> Valor C: http://schemas.microsoft.com/...|  
|\<XmlDP:Query xmlns:xmldp = "http://schemas.microsoft.com/sqlserver/2005/02/reporting/XmlDPQuery" xmlns:ns = "http://schemas.microsoft.com/..." ><br /><br /> \<XmlDP:ElementPath > raíz {}/ns:Element2 / nodo\</xmldp:ElementPath ><br /><br /> \</XmlDP:Query >|Valor D<br /><br /> Valor E<br /><br /> Valor F|  
  
#### <a name="xml-document-dpnamespacexml"></a>Documento XML: DPNamespace.xml  
 Puede copiar este documento XML y guardarlo en una dirección URL disponible para el Diseñador de informes con objeto de poder usarlo como origen de datos XML, por ejemplo, http://localhost/DPNamespace.xml.  
  
```  
<Root xmlns:ns="http://schemas.microsoft.com/...">  
   <ns:Element1>  
      <Node>Value A</Node>  
      <Node>Value B</Node>  
      <Node>Value C</Node>  
   </ns:Element1>  
   <ns:Element2>  
      <Node>Value D</Node>  
      <Node>Value E</Node>  
      <Node>Value F</Node>  
   </ns:Element2>  
</Root>  
```  
  
## <a name="see-also"></a>Vea también  
 [Tipo de conexión XML &#40;SSRS&#41;](xml-connection-type-ssrs.md)   
 [Tutoriales de Reporting Services &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md)  
  
  
