---
title: Aplicar inmediatamente los permisos de los miembros (Master Data Services) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- members [Master Data Services], applying permissions immediately
- permissions [Master Data Services], applying member permissions immediately
ms.assetid: 5b16de66-5c39-49f5-992f-402a9eb319aa
caps.latest.revision: 6
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: a3ac0d4510b77c5e0c6fe95ff7cbf2c6aae433be
ms.contentlocale: es-es
ms.lasthandoff: 09/07/2017

---
# <a name="immediately-apply-member-permissions-master-data-services"></a>Aplicar inmediatamente los permisos de los miembros (Master Data Services)
  En [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], en lugar de esperar a que la seguridad de los miembros se aplique a intervalos normales, puede aplicar los permisos de miembro inmediatamente.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para realizar este procedimiento:  
  
-   Debe tener permiso para ejecutar el procedimiento almacenado mds.udpSecurityMemberProcessRebuildModel en la base de datos [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Para obtener más información, consulte [Seguridad de objetos de base de datos &#40;Master Data Services&#41;](../master-data-services/database-object-security-master-data-services.md).  
  
### <a name="to-immediately-apply-hierarchy-member-permissions"></a>Para aplicar inmediatamente permisos de miembro de jerarquía  
  
1.  Abra [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] y conéctese a la instancia de [!INCLUDE[ssDE](../includes/ssde-md.md)] para la base de datos de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  Cree una nueva consulta.  
  
3.  Escriba el siguiente texto y reemplace *database* con el nombre de su base de datos y *Model_Name* con el nombre del modelo.  
  
    ```  
    USE [database];  
    GO  
  
    DECLARE @Model_ID INT;  
    SELECT @Model_ID = ID FROM mdm.tblModel WHERE [Name] = N'Model_Name';  
    EXEC [mdm].[udpSecurityMemberProcessRebuildModel] @Model_ID=@Model_ID, @ProcessNow=1;  
    GO  
    ```  
  
4.  Ejecuta la consulta.  
  
## <a name="see-also"></a>Vea también  
 [Asignar los permisos de los miembros de una jerarquía &#40;Master Data Services&#41;](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [Permisos de miembros de la jerarquía &#40;Master Data Services&#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)  
  
  

