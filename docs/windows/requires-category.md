---
title: requires_category | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.requires_category
dev_langs:
- C++
helpviewer_keywords:
- requires_category attribute
ms.assetid: a645fdc6-1ef5-414d-8c56-5fe2686d4687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9ddcfe01ec5bd838a84ddad351f43802a8142b44
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606099"
---
# <a name="requirescategory"></a>requires_category
Spécifie les catégories de composant requis de la classe cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ requires_category(   
  requires_category  
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *requires_category*  
 ID de la catégorie obligatoire.  
  
## <a name="remarks"></a>Notes  
 Le **requires_category** attribut C++ Spécifie les catégories de composants requis par la classe cible. Pour plus d’informations, consultez [REQUIRED_CATEGORY](../atl/reference/category-macros.md#required_category).  
  
 Cet attribut exige que l’attribut [coclass](../windows/coclass.md), [progid](../windows/progid.md)ou [vi_progid](../windows/vi-progid.md) (ou un autre attribut qui implique l’un de ceux-ci) soit également appliqué au même élément.  
  
## <a name="example"></a>Exemple  
 Le code suivant requiert que l’objet implémente la catégorie de contrôle.  
  
```cpp  
// cpp_attr_ref_requires_category.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="MyLibrary")];  
  
[ coclass, requires_category("CATID_Control"),  
  uuid("1e1a2436-f3ea-4ff3-80bf-5409370e8144")]  
class CMyClass {};  
```  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|**classe**, **struct**|  
|**Renouvelable**|Non|  
|**Attributs requis**|Un ou plusieurs des opérations suivantes : `coclass`, `progid`, ou `vi_progid`.|  
|**Attributs non valides**|Aucun.|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs COM](../windows/com-attributes.md)   
 [implements_category](../windows/implements-category.md)   