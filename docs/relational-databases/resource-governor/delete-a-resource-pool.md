---
title: "Eliminación de un grupo de recursos de servidor | Microsoft Docs"
ms.custom: 
ms.date: 03/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Resource Governor, resource pool delete
- resource pools [SQL Server], delete
ms.assetid: 3bdd348b-6582-4ffa-80ef-d49e50596ce5
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 857ce687209066520bb2ec552b93fd46d547b38e
ms.contentlocale: es-es
ms.lasthandoff: 06/22/2017

---
# <a name="delete-a-resource-pool"></a>Eliminar un grupo de recursos de servidor
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Puede eliminar un grupo de recursos de servidor utilizando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o Transact-SQL.  
  
-   **Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)  
  
-   **To delete a resource pool, using:** [SQL Server Management Studio](#DelRPSSMS), [Transact-SQL](#DelRPTSQL)  
  
##  <a name="BeforeYouBegin"></a> Antes de empezar  
 No se puede eliminar un grupo de recursos de servidor si contiene grupos de cargas de trabajo.  
  
###  <a name="LimitationsRestrictions"></a> Limitaciones y restricciones  
 No se pueden eliminar los grupos de recursos de servidor predeterminados o internos del regulador de recursos. No se puede eliminar un grupo de recursos de servidor si contiene grupos de cargas de trabajo. Para obtener más información, consulte [Delete a Workload Group](../../relational-databases/resource-governor/delete-a-workload-group.md).  
  
###  <a name="Permissions"></a> Permisos  
 Para eliminar un grupo de recursos de servidor se requiere un permiso CONTROL SERVER.  
  
##  <a name="DelRPSSMS"></a> Eliminar un grupo de recursos de servidor mediante el Explorador de objetos  
 **Para eliminar un grupo de recursos de servidor mediante SQL Server Management Studio**  
  
1.  En [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], abra el Explorador de objetos y expanda de forma recursiva el nodo **Administración** hasta e incluyendo el nodo **Regulador de recursos**.  
  
2.  Haga clic con el botón derecho en el grupo de recursos que va a eliminar y luego haga clic en **Eliminar**.  
  
3.  En la ventana **Eliminar objeto** aparece el grupo de recursos de servidor en la lista **Objeto que se va a eliminar** . Para eliminar el grupo de recursos de servidor, haga clic en **Aceptar**.  
  
    > [!NOTE]  
    >  Si el grupo de recursos de servidor que intenta eliminar contiene un grupo de cargas de trabajo, esta acción provocará un error.  
  
##  <a name="DelRPTSQL"></a> Eliminar un grupo de recursos de servidor mediante Transact-SQL  
 **Para eliminar un grupo de recursos de servidor mediante Transact-SQL**  
  
1.  Ejecute la instrucción **DROP RESOURCE POOL** o **DROP EXTERNAL RESOURCE POOL** y especifique el nombre del grupo de recursos que quiere eliminar.  
  
2.  Ejecute la instrucción **ALTER RESOURCE GOVERNOR RECONFIGURE** .  
  
### <a name="example-transact-sql"></a>Ejemplo (Transact-SQL)  
 En el ejemplo siguiente se quita un grupo de cargas de trabajo denominado `poolAdhoc`.  
  
```  
DROP RESOURCE POOL poolAdhoc;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Vea también  
 [Regulador de recursos](../../relational-databases/resource-governor/resource-governor.md)   
 [Resource Governor Resource Pool](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [Crear un grupo de recursos de servidor](../../relational-databases/resource-governor/create-a-resource-pool.md)   
 [Cambiar la configuración del grupo de recursos de servidor](../../relational-databases/resource-governor/change-resource-pool-settings.md)   
 [Grupos de cargas de trabajo del regulador de recursos](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [Función clasificadora del regulador de recursos](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [DROP RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)   
 [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)   
 [DROP EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-external-resource-pool-transact-sql.md)   
 [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)   
 [ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)  
  
  

