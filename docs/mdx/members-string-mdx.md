---
title: Los miembros (cadena) (MDX) | Documentos de Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Members
dev_langs:
- kbMDX
helpviewer_keywords:
- Members function
ms.assetid: 21fca354-448b-4b05-93f4-111bde1568f1
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 14ab54616fdfeb85cb5b45f1e6d77b8e5c475c41
ms.contentlocale: es-es
ms.lasthandoff: 08/02/2017

---
# <a name="members-string-mdx"></a>Members (String) (MDX)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

  Devuelve un miembro especificado por una expresión de cadena.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
Members(Member_Name)   
```  
  
## <a name="arguments"></a>Argumentos  
 *Member_Name*  
 Expresión de cadena válida que especifica un nombre de miembro.  
  
## <a name="remarks"></a>Comentarios  
 El **miembros (cadena)** función devuelve un único miembro cuyo nombre se especifica. Normalmente, se utiliza el **miembros (cadena)** función con funciones externas, lo que ofrece a los **miembros (cadena)** función una cadena que identifica un miembro, y el **miembros (cadena)** función devuelve el valor de este miembro especificado.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa el **miembros (cadena)** función para convertir la cadena especificada en un miembro válido y, a continuación, devuelve la medida predeterminada para el miembro especificado en la cadena. La cadena se especifica entre comillas simples. La medida predeterminada es la medida Reseller Sales Amount.  
  
```  
SELECT Members ('[Geography].[Geography].[Country].&[United States] ') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de funciones MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

