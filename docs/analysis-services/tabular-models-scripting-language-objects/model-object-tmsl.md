---
title: Objeto de modelo (TMSL) | Documentos de Microsoft
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6f60b0998dd344cdc3151da1a1c8920495b36917
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2018
ms.locfileid: "34043209"
---
# <a name="model-object-tmsl"></a>Objeto de modelo (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Define un modelo Tabular. Hay un modelo por base de datos y una base de datos que se pueden especificar en un determinado comando. Un objeto de base de datos es el objeto primario.  
  
 Las definiciones de modelo son demasiado grandes para reproducir toda la sintaxis de un tema. Por esta razón, una las partes principales para resaltar la sintaxis parcial puede encontrarse a continuación, con vínculos a los objetos secundarios.  
  
 Quizás la mejor manera de comprender una definición de modelo es empezar con un modelo Tabular que conoce bien. Use la **ver código** opción en herramientas de datos de SQL Server para ver su definición. Recuerde que debe instalar a un editor de JSON para que pueda ver el código. Puede obtener un editor de JSON en Visual Studio [descargar la edición Community](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx) o de otra edición de Visual Studio.  
  
> [!NOTE]  
>  En los scripts, puede hacer referencia a una base de datos en el momento. Para cualquier objeto que no sea la propia base de datos, la propiedad de base de datos es opcional si especifica el modelo. Hay una asignación uno a uno entre un modelo y una base de datos que puede usarse para deducir el nombre de la base de datos si explícitamente no se proporciona.   
> De forma similar, puede dejar al margen modelo, establecer sus propiedades en la base de datos.  
  
## <a name="object-definition"></a>Definición del objeto  
 Todos los objetos tienen un conjunto común de propiedades, incluidos el nombre, tipo, descripción, una colección de propiedades y las anotaciones. **Modelo** objetos también tienen las siguientes propiedades.  
  
 storageLocation  
 La ubicación en disco donde se va a colocar el modelo.  
  
 defaultMode  
 El método predeterminado para hacer que los datos estén disponibles en la partición.  
  
 defaultDataView  
 Para los modelos en el modo DirectQuery, esta propiedad determina qué particiones se utilizan para ejecutar consultas en el modelo.  Los valores válidos son Full y ejemplo.  
  
 referencia cultural  
 Referencia cultural que se va a usar para dar formato.  
  
 collation  
 La secuencia de intercalación. Vea [escenarios de globalización para Analysis Services](../../analysis-services/globalization-scenarios-for-analysis-services.md) para obtener más información.  
  
 tablas  
 La colección completa de tablas en el modelo, incluidas las particiones, las columnas, medidas, KPI y anotaciones. Vea [Tables, objeto &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md) para obtener más información.  
  
 relaciones  
 Especifica la relación entre cada par de tablas, incluidas las propiedades que configurar la dirección del filtro y la seguridad. Vea [objeto relaciones &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/relationships-object-tmsl.md) para obtener más información.  
  
 orígenes de datos  
 Una o varias conexiones a bases de datos externos que proporciona datos para el modelo o utilizar para pasan a través de consultas. Vea [objeto de orígenes de datos &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md) para obtener más información.  
  
 roles  
 Objetos que asocian un permiso de base de datos, cuentas de usuario registrado y, opcionalmente, filtros de seguridad en DAX para control de acceso personalizado.  
  
## <a name="usage"></a>Uso  
 **Modelo** objetos contienen un modelo completo. Debe especificar un modelo o su objeto de base de datos primario en la mayoría de los comandos.  
  
 Al crear, reemplazar o modificar un objeto de modelo, especificar todas las propiedades de lectura y escritura de la definición del objeto. Omisión de una propiedad de lectura y escritura se considera una operación de eliminación.  
  
## <a name="partial-syntax"></a>Sintaxis parcial  
 Dado que esta definición de objeto es tan grande, se muestran solo las propiedades primer nivel. Vea [definiciones de objetos Tabular Model Scripting Language &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/tmsl-reference-tabular-objects.md) para obtener una lista de objetos secundarios.  
  
```  
    "model": {  
      "description": "Model object of a Tabular database",  
      "type": "object",  
      "properties": {  
          "name": {  },  
          "description": {  },  
         "storageLocation": {  },  
         "defaultMode":  {  },  
         "defaultDataView": {  },  
         "culture": {  },  
         "collation": {  },  
         "annotations": {  },  
         "tables": {  },  
         "relationships": {  },  
         "dataSources": {  },  
         "perspectives": {  },  
            "cultures": {  },  
         "roles": {  }  
    }  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Referencia de Tabular Model Scripting Language [TMSL])](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Nivel de compatibilidad para modelos tabulares de Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
