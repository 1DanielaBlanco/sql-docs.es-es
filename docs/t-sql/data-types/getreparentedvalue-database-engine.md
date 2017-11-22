---
title: GetReparentedValue (motor de base de datos) | Documentos de Microsoft
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Reparent_TSQL
- Reparent
dev_langs: TSQL
helpviewer_keywords: Reparent [Database Engine]
ms.assetid: f47f8e25-08ef-498b-84f4-a317aca1f358
caps.latest.revision: "25"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e0b054e9651cce9a486d4acf9e997a601114e98a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="getreparentedvalue-database-engine"></a>GetReparentedValue (motor de base de datos)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Devuelve un nodo cuya ruta de acceso desde la raíz es la ruta de acceso a *newRoot*, seguido de la ruta de acceso de *oldRoot* a *esto*.
  
## <a name="syntax"></a>Sintaxis  
  
```sql
-- Transact-SQL syntax  
node. GetReparentedValue ( oldRoot, newRoot )  
```  
  
```sql
-- CLR syntax  
SqlHierarchyId GetReparentedValue ( SqlHierarchyId oldRoot , SqlHierarchyId newRoot )  
```  
  
## <a name="arguments"></a>Argumentos  
*oldRoot*  
A **hierarchyid** que es el nodo que representa el nivel de la jerarquía que va a modificarse.
  
*newRoot*  
A **hierarchyid** que representa el nodo que va a reemplazar el *oldRoot* sección del nodo actual con el fin de mover el nodo.
  
## <a name="return-types"></a>Tipos devueltos  
**Tipo: hierarchyid devuelto de SQL Server**
  
**Tipo: SqlHierarchyId devuelto de CLR**
  
## <a name="remarks"></a>Comentarios  
Puede utilizarse para modificar el árbol moviendo los nodos de *oldRoot* a *newRoot*. GetReparentedValue se puede utilizar para mover un nodo de una jerarquía a una ubicación nueva en la jerarquía. El **hierarchyid** representa el tipo de datos, aunque no exige la estructura jerárquica. Los usuarios deben asegurarse de que el identificador hierarchyid se estructura de forma apropiada para la nueva ubicación. Un índice único en el **hierarchyid** tipo de datos puede ayudar a evitar las entradas duplicadas. Para obtener un ejemplo de mover un subárbol completo, vea [datos jerárquicos &#40; SQL Server &#41; ](../../relational-databases/hierarchical-data-sql-server.md).
  
## <a name="examples"></a>Ejemplos  
  
### <a name="a-comparing-two-node-locations"></a>A. Comparar dos ubicaciones de nodo  
En el ejemplo siguiente se muestra el identificador hierarchyid actual de un nodo. También se muestra cuál el **hierarchyid** del nodo sería si el nodo se pasó a ser un descendiente de la  **@NewParent**  nodo. Utiliza el método `ToString()` para mostrar las relaciones jerárquicas.
  
```sql
DECLARE @SubjectEmployee hierarchyid , @OldParent hierarchyid, @NewParent hierarchyid  
SELECT @SubjectEmployee = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\gail0' ;  
SELECT @OldParent = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\roberto0' ; -- who is /1/1/  
SELECT @NewParent = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\wanida0' ; -- who is /2/3/  
  
SELECT OrgNode.ToString() AS Current_OrgNode_AS_Text,   
(@SubjectEmployee. GetReparentedValue(@OldParent, @NewParent) ).ToString() AS Proposed_OrgNode_AS_Text,  
OrgNode AS Current_OrgNode,  
@SubjectEmployee. GetReparentedValue(@OldParent, @NewParent) AS Proposed_OrgNode,  
*  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode = @SubjectEmployee ;  
GO  
```  
  
### <a name="b-updating-a-node-to-a-new-location"></a>B. Actualizar un nodo a una ubicación nueva  
En el ejemplo siguiente se utiliza `GetReparentedValue()` en una instrucción UPDATE para mover un nodo de una ubicación anterior a una ubicación nueva en la jerarquía:
  
```sql
DECLARE @SubjectEmployee hierarchyid , @OldParent hierarchyid, @NewParent hierarchyid  
SELECT @SubjectEmployee = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\gail0' ; -- Node /1/1/2/  
SELECT @OldParent = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\roberto0' ; -- Node /1/1/  
SELECT @NewParent = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\wanida0' ; -- Node /2/3/  
  
UPDATE HumanResources.EmployeeDemo  
SET OrgNode = @SubjectEmployee. GetReparentedValue(@OldParent, @NewParent)   
WHERE OrgNode = @SubjectEmployee ;  
  
SELECT OrgNode.ToString() AS Current_OrgNode_AS_Text,   
*  
FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\gail0' ; -- Now node /2/3/2/  
```  
  
### <a name="c-clr-example"></a>C. Ejemplo de CLR  
El fragmento de código siguiente llama al método de () de GetReparentedValue:
  
```sql
this. GetReparentedValue(oldParent, newParent)  
```  
  
## <a name="see-also"></a>Vea también
[Referencia de los métodos del tipo de datos hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Datos jerárquicos &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  
