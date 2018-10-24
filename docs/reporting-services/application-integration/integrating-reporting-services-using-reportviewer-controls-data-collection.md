---
title: Recopilación de datos del control ReportViewer 2016 | Microsoft Docs
ms.date: 09/18/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 68e5a4c9789a6c0485433a3199d8d6a03c2a90d5
ms.sourcegitcommit: a251adad8474b477363df6a121431b837f22bf77
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47864343"
---
# <a name="integrating-reporting-services-using-reportviewer-controls---data-collection"></a>Integración de Reporting Services con los controles ReportViewer: recopilación de datos

El control recopila datos de uso anónimos para comprender mejor cómo los clientes usan el producto. Los datos de uso permiten que el desarrollo futuro se centre en las mejoras que sean más relevantes para los clientes.

En la [declaración de privacidad](http://go.microsoft.com/fwlink/?LinkID=868444) encontrará una explicación de las prácticas de recopilación y uso de datos de Microsoft SQL Server y el Visor de informes.

## <a name="opting-out-of-data-collection"></a>Exclusión de la recopilación de datos

Se puede deshabilitar la recopilación de datos de uso a través de la propiedad ```EnableTelemetry```.

```
<rsweb:ReportViewer ID="ReportViewer1" runat="server" EnableTelemetry="false">
</rsweb:ReportViewer>
```

O mediante pragmática antes de representar el control.
    
```
protected void Page_Load(object sender, EventArgs e)
{
    ReportViewer1.EnableTelemetry = false;
}
```
## <a name="see-also"></a>Vea también

[Usar el control ReportViewer de WebForms](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)  
[Integración de Reporting Services con los controles del Visor de informes](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 



