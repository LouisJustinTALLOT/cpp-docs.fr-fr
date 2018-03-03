---
title: Classe de CSimpleArrayEqualHelper | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 57e5b40785bda57a4d5578bb998c4c97336246be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="csimplearrayequalhelper-class"></a>Classe de CSimpleArrayEqualHelper
Cette classe est une application d’assistance pour le [CSimpleArray](../../atl/reference/csimplearray-class.md) classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class CSimpleArrayEqualHelper
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Une classe dérivée.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CSimpleArrayEqualHelper::IsEqual](#isequal)|(Statique) Teste si deux `CSimpleArray` éléments pour l’égalité de l’objet.|  
  
## <a name="remarks"></a>Notes  
 Cette classe de traits est un supplément à la `CSimpleArray` classe. Il fournit une méthode de comparaison de deux éléments stockés dans un `CSimpleArray` objet. Par défaut, les éléments sont comparés à l’aide de **operator=()**, mais si le tableau contient les types de données complexes qui n’ont pas leur propre opérateur d’égalité, vous devez substituer cette classe.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlsimpcoll.h  
  
##  <a name="isequal"></a>CSimpleArrayEqualHelper::IsEqual  
 Teste si deux `CSimpleArray` éléments pour l’égalité de l’objet.  
  
```
static bool IsEqual(
    const T& t1,
    const T& t2);
```  
  
### <a name="parameters"></a>Paramètres  
 *T1*  
 Un objet de type T.  
  
 *T2*  
 Un objet de type T.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true si les éléments sont égaux, false dans le cas contraire.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CSimpleArray](../../atl/reference/csimplearray-class.md)   
 [Classe de CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
