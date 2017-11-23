---
title: "Este libro contiene una o más consultas que actualizan los datos externos | Documentos de Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: power-pivot-sharepoint
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: aa65c992-eb41-4032-9e11-a9ba871b6a3c
caps.latest.revision: "8"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 882a0dca2f6c2c443507bc5b4d54820711e55ae7
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2017
---
# <a name="this-workbook-contains-one-or-more-queries-that-refresh-external-data"></a>Este libro contiene una o más consultas que actualizan los datos externos
  En los libros de Excel que contienen datos [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , Excel Services muestra esta advertencia cuando detecta información de conexión y le indica que habilite o deshabilite las consultas para este libro.  
  
## <a name="details"></a>Detalles  
  
|||  
|-|-|  
|Nombre del producto|[!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] para SharePoint|  
|Versión del producto|[!INCLUDE[ssKilimanjaro_md](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11_md](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14_md](../../includes/sssql14-md.md)]|  
|Causa|Servicios de Excel se configura para advertir al realizar la actualización de datos.|  
|Texto del mensaje|Este libro contiene al menos una consulta que actualiza los datos externos. Un usuario malintencionado podría diseñar una consulta para obtener acceso a información confidencial y distribuirla a los otros usuarios o llevar a cabo otras acciones perjudiciales.<br /><br /> Si la fuente de este libro es de confianza, haga clic en Sí para permitir consultas a datos externos al libro. Si no está seguro, haga clic en No de forma que los cambios no se implementen en el libro.<br /><br /> ¿Desea permitir las consultas a los datos externos de este libro?|  
  
## <a name="explanation"></a>Explicación  
 [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] contienen cadenas de conexión de datos incrustadas que usa Excel para comunicarse con un servidor de [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] externo que carga y calcula los datos. Cuando se habilitan las advertencias de la actualización de datos, Servicios de Excel detecta esta cadena de conexión y advierte al usuario en consecuencia.  
  
 Para filtrar y segmentar los datos [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] del libro, las consultas deben estar habilitadas. Asegúrese de habilitar las consultas solo para aquellos libros [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] en los que confíe.  
  
## <a name="user-action"></a>Acción del usuario  
 Haga clic en **Sí** para habilitar las consultas.  
  
 También puede cambiar la configuración de forma que la advertencia de la actualización ya no se produzca:  
  
1.  En Administración central, en Administración de aplicaciones, haga clic en **Administrar aplicaciones de servicio**.  
  
2.  Haga clic en **Aplicación de Servicios de Excel**.  
  
3.  Haga clic en **Ubicación de archivo de confianza**.  
  
4.  Haga clic en **http://** o en la ubicación que quiera configurar.  
  
5.  En Datos externos, desactive la casilla de **Advertencia en actualización de datos**.  
  
6.  Haga clic en **Aceptar**.  
  
 O bien, puede crear una nueva ubicación de confianza para los sitios que contienen los libros [!INCLUDE[ssGemini_md](../../includes/ssgemini-md.md)] y, a continuación, modificar la configuración solo para ese sitio. Para más información, vea [Create a trusted location for Power Pivot sites in Central Administration](../../analysis-services/power-pivot-sharepoint/create-a-trusted-location-for-power-pivot-sites-in-central-administration.md).  
  
  
