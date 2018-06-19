---
title: Classe de CSimpleArrayEqualHelperFalse | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse::IsEqual
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e22d67634f29b60bdc983c892c5fe266df61d08
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358199"
---
# <a name="csimplearrayequalhelperfalse-class"></a>Classe de CSimpleArrayEqualHelperFalse
Cette classe est une application d’assistance pour le [CSimpleArray](../../atl/reference/csimplearray-class.md) classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class CSimpleArrayEqualHelperFalse
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Une classe dérivée.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CSimpleArrayEqualHelperFalse::IsEqual](#isequal)|(Statique) Retourne la valeur false.|  
  
## <a name="remarks"></a>Notes  
 Cette classe de traits est un complément à la `CSimpleArray` classe. Informatique toujours retourne false et, en outre, appellera `ATLASSERT` avec un argument de la valeur false si elle n’est jamais référencée. Dans les situations où le test d’égalité n’est pas suffisamment défini, cette classe permet à un tableau contenant les éléments pour ne fonctionne pas correctement pour la plupart des méthodes, mais échouer de façon bien définie pour les méthodes qui dépendent des comparaisons telles que [CSimpleArray :: Rechercher](../../atl/reference/csimplearray-class.md#find).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlsimpcoll.h  
  
##  <a name="isequal"></a>  CSimpleArrayEqualHelperFalse::IsEqual  
 Retourne false.  
  
```
static bool IsEqual(const T&, const T&);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne false.  
  
### <a name="remarks"></a>Notes  
 Cette méthode retourne toujours false et appelle `ATLASSERT` avec un argument de la valeur false si référencé. L’objectif de `CSimpleArrayEqualHelperFalse::IsEqual` consiste à forcer les méthodes à l’aide de comparaisons échouer de façon bien définie lors de tests d’égalité n’ont pas été définies correctement.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
