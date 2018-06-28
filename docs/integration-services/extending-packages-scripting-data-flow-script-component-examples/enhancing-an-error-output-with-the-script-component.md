---
title: Mejorar una salida de errores con el componente de script | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- transformations [Integration Services], components
- Script component [Integration Services], examples
- error outputs [Integration Services], enhancing
- Script component [Integration Services], transformation components
ms.assetid: f7c02709-f1fa-4ebd-b255-dc8b81feeaa5
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f7f310cc4260bfc621436778d6363dc8cb8276b3
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2018
ms.locfileid: "35406377"
---
# <a name="enhancing-an-error-output-with-the-script-component"></a>Mejorar una salida de errores con el componente de script
  De forma predeterminada, las dos columnas adicionales en una salida de errores de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], ErrorCode y ErrorColumn, solo contienen códigos numéricos que representan un número de error y el id. de la columna en la que se produjo el error. Estos valores numéricos pueden tener un uso limitado sin la descripción del error y el nombre de columna correspondientes.  
  
 En este tema se describe cómo agregar la descripción del error y el nombre de la columna a los datos de salida del error existentes en el flujo de datos mediante el componente de script. En el ejemplo se agrega la descripción del error que corresponde a un determinado código de error de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] predefinido mediante el método <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> de la interfaz <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>, disponible a través de la propiedad <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> del componente de script. A continuación, en el ejemplo se agrega el nombre de columna que corresponde al id. de linaje capturado mediante el método <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData130.GetIdentificationStringByID%2A> de la misma interfaz.  
  
> [!NOTE]  
>  Si desea crear un componente que pueda reutilizar más fácilmente en varias tareas de flujo de datos y varios paquetes, puede utilizar el código de este ejemplo de componente de script como punto de inicio para el componente de flujo de datos personalizado. Para obtener más información, vea [Desarrollar un componente de flujo de datos personalizado](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo que aparece aquí se utiliza un componente de script configurado como transformación para agregar la descripción del error y el nombre de columna a los datos de salida de error existentes en el flujo de datos.  
  
 Para obtener más información acerca de cómo configurar el componente de script para su uso como transformación en el flujo de datos, vea [Crear una transformación sincrónica con el componente de script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) y [Crear una transformación asincrónica con el componente de script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md).  
  
#### <a name="to-configure-this-script-component-example"></a>Para configurar este ejemplo de componente de script  
  
1.  Antes de crear el nuevo componente de script, configure un componente de nivel superior en el flujo de datos para redirigir las filas a su salida de error cuando se produce un error o truncamiento. Con fines de comprobación, puede que desee configurar un componente de manera que garantice que se van a producir errores; por ejemplo mediante la configuración de una transformación de búsqueda entre dos tablas donde se producirá un error en la búsqueda.  
  
2.  Agregue un nuevo componente de script a la superficie del diseñador de flujo de datos y configúrelo como una transformación.  
  
3.  Conecte la salida de error del componente de nivel superior al nuevo componente de script.  
  
4.  Abra el **Editor de transformación Script** y en la página **Script**, para la propiedad **ScriptLanguage**, seleccione el lenguaje de script.  
  
5.  Haga clic en **Editar script[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para abrir el IDE de**  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Tools for Applications (VSTA) y agregue el código de ejemplo que se muestra a continuación.  
  
6.  Cierre VSTA.  
  
7.  En el Editor de transformación Script, en la página **Columnas de entrada**, seleccione las columnas ErrorCode y Error Column.  
  
8.  En la página **Entradas y salidas**, agregue dos nuevas columnas.  
  
    -   Agregue una nueva columna de salida de tipo **String** denominada **ErrorDescription**. Aumente la longitud predeterminada de la nueva columna a 255 para admitir mensajes largos.  
  
    -   Agregue otra columna de salida nueva de tipo **String** denominada **ColumnName**. Aumente la longitud predeterminada de la nueva columna a 255 para admitir valores largos.  
  
9. Cierre el **Editor de transformación Script**.  
  
10. Adjunte la salida del componente de script a un destino conveniente. Para pruebas ad hoc, la manera más fácil de configurar es mediante un destino de archivo plano.  
  
11. Ejecute el paquete.  
  
```vb  
Public Class ScriptMain  
    Inherits UserComponent  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
      Row.ErrorDescription = _  
        Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
  
      Dim componentMetaData130 = TryCast(Me.ComponentMetaData, IDTSComponentMetaData130)  
      If componentMetaData130 IsNot Nothing Then  
        Row.ColumnName = componentMetaData130.GetIdentificationStringByID(Row.ErrorColumn)  
         End If  
  
    End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain:  
    UserComponent  
{  
    public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
  
      Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
  
      var componentMetaData130 = this.ComponentMetaData as IDTSComponentMetaData130;  
      if (componentMetaData130 != null)  
        {  
            Row.ColumnName = componentMetaData130.GetIdentificationStringByID(Row.ErrorColumn);  
        }  
  
    }  
}  
  
```  
  
## <a name="see-also"></a>Ver también  
 [Control de errores en los datos](../../integration-services/data-flow/error-handling-in-data.md)   
 [Usar las salidas de error en un componente de flujo de datos](../../integration-services/extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md)   
 [Crear una transformación sincrónica con el componente de script](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)   
  
  
