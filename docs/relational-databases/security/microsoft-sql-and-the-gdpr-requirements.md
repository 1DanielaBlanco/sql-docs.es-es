---
title: Microsoft SQL y los requisitos del RGPD| Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.reviewer: ''
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: article
caps.latest.revision: 2
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 228cc003bfdd61bd0ead16e34810e52caf143438
ms.sourcegitcommit: 094c46e7fa6de44735ed0040c65a40ec3d951b75
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2018
---
# <a name="guide-to-enhancing-privacy-and-addressing-gdpr-requirements-with-the-microsoft-sql-platform"></a>Guía para la mejora de la privacidad y requisitos del RGPD con la plataforma de Microsoft SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

## <a name="summary"></a>Resumen
El 25 de mayo de 2018 entrará en vigor una ley de privacidad europea que establecerá una nueva barrera global en materia de derechos de privacidad, seguridad y cumplimiento. El Reglamento general de protección de datos (o RGPD) trata fundamentalmente de proteger y habilitar los derechos de privacidad de las personas y establece requisitos de privacidad estrictos y globales que regulan cómo se administran y protegen los datos personales respetando a su vez la elección personal. 

Los clientes de Microsoft SQL que están sujetos al RGPD (ya sea al administrar bases de datos basadas en la nube, locales o ambas) deben asegurarse de que los datos obtenidos en sus sistemas de bases de datos se traten y protejan adecuadamente de acuerdo con los principios del RGPD. Esto significa que muchos clientes tendrán que revisar o modificar sus procedimientos de control de datos y administración de bases de datos. Sobre todo, tendrán que centrarse en la seguridad del procesamiento de datos tal y como se estipula en el RGPD.

Las tecnologías basadas en Microsoft SQL ofrecen muchas funcionalidades de seguridad integradas que pueden ayudar a reducir los riesgos en los datos y mejorar la protección y la funcionalidades de administración de los datos en el nivel de base de datos y más allá. En este documento se examinan estas funcionalidades y se comparten algunos de los enfoques de Microsoft en los que se usa Microsoft SQL para lograr los objetivos de privacidad de datos del RGPD.
   
  
**Autor:** Ronit Reger

**Revisores técnicos:** Conor Cunningham; Joachim Hammer; Shai Kariv; Julie Koesmarno; Alice Kupcik; Ron Matchoro; Gilad Mittelman; Dan Rediske; Tomer Weisberg 
  
**Publicación:** mayo de 2017  
  
**Se aplica a:** SQL Server (todas las versiones), Azure SQL Database, Azure SQL Data Warehouse, Analytics Platform System 
  
Para consultar el documento, descargue [Guide to enhancing privacy and addressing GDPR requirements with the Microsoft SQL platform](http://download.microsoft.com/download/4/9/4/4948194B-A613-49ED-90A5-5144313549AB/microsoft-sql-and-the-gdpr.pdf) (Guía para la mejora de la privacidad y direccionamiento de requisitos del RGPD con la plataforma de Microsoft SQL).   
