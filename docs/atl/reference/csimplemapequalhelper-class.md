---
title: Classe de CSimpleMapEqualHelper | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b4bfef99d12ae724c2ca6e70375f08a8dc1fb15b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361838"
---
# <a name="csimplemapequalhelper-class"></a>Classe de CSimpleMapEqualHelper
Cette classe est une application d’assistance pour le [CSimpleMap](../../atl/reference/csimplemap-class.md) classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class TKey, class TVal>  
class CSimpleMapEqualHelper
```  
  
#### <a name="parameters"></a>Paramètres  
 `TKey`  
 L’élément clé.  
  
 `TVal`  
 L’élément de valeur.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|(Statique) Teste l’égalité de deux clés.|  
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|(Statique) Teste l’égalité de deux valeurs.|  
  
## <a name="remarks"></a>Notes  
 Cette classe de traits est un supplément à la `CSimpleMap` classe. Il fournit des méthodes pour la comparaison de deux `CSimpleMap` éléments (plus précisément, les composants de clé et valeur) pour l’égalité de l’objet. Par défaut, les clés et valeurs sont comparées à l’aide de `operator==()`, mais si le mappage contient des types de données complexes qui n’ont pas leur propre opérateur d’égalité, cette classe peut être substituée pour fournir la fonctionnalité supplémentaire.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlsimpcoll.h  
  
##  <a name="isequalkey"></a>  CSimpleMapEqualHelper::IsEqualKey  
 Teste l’égalité de deux clés.  
  
```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```  
  
### <a name="parameters"></a>Paramètres  
 `k1`  
 La première clé.  
  
 `k2`  
 La seconde clé.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true si les clés sont égales.  
  
##  <a name="isequalvalue"></a>  CSimpleMapEqualHelper::IsEqualValue  
 Teste l’égalité de deux valeurs.  
  
```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```  
  
### <a name="parameters"></a>Paramètres  
 *V1*  
 Première valeur.  
  
 *V2*  
 Seconde valeur.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true si les valeurs sont égales, false dans le cas contraire.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
