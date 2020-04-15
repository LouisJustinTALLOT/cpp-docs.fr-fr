---
title: Classe CRBMap
ms.date: 11/04/2016
f1_keywords:
- CRBMap
- ATLCOLL/ATL::CRBMap
- ATLCOLL/ATL::CRBMap::CRBMap
- ATLCOLL/ATL::CRBMap::Lookup
- ATLCOLL/ATL::CRBMap::RemoveKey
- ATLCOLL/ATL::CRBMap::SetAt
helpviewer_keywords:
- CRBMap class
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
ms.openlocfilehash: 9e367ccc875eedf63e4f47018598662af2dfcf7d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331397"
---
# <a name="crbmap-class"></a>Classe CRBMap

Cette classe représente une structure de cartographie, à l’aide d’un arbre binaire Rouge-Noir.

## <a name="syntax"></a>Syntaxe

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CRBMap : public CRBTree<K, V, KTraits, VTraits>
```

#### <a name="parameters"></a>Paramètres

*K*<br/>
Le type d’élément clé.

*V*<br/>
Le type d’élément de valeur.

*Les KTraits*<br/>
Le code utilisé pour copier ou déplacer des éléments clés. Voir [CElementTraits Class](../../atl/reference/celementtraits-class.md) pour plus de détails.

*VTraits*<br/>
Le code utilisé pour copier ou déplacer des éléments de valeur.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CRBMap::CRBMap](#crbmap)|Constructeur.|
|[CRBMap::CRBMap](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRBMap::Lookup](#lookup)|Appelez cette méthode pour rechercher des `CRBMap` clés ou des valeurs dans l’objet.|
|[CRBMap::RemoveKey](#removekey)|Appelez cette méthode pour supprimer `CRBMap` un élément de l’objet, compte tenu de la clé.|
|[CRBMap::SetAt](#setat)|Appelez cette méthode pour insérer une paire d’éléments dans la carte.|

## <a name="remarks"></a>Notes

`CRBMap`fournit un soutien pour un tableau de cartographie de n’importe quel type donné, la gestion d’un tableau ordonné d’éléments clés et leurs valeurs associées. Chaque clé ne peut avoir qu’une seule valeur associée. Les éléments (composés d’une clé et d’une valeur) sont stockés dans une structure d’arbre binaire, à l’aide de la méthode [CRBMap::SetAt.](#setat) Les éléments peuvent être supprimés à l’aide de la méthode [CRBMap::RemoveKey,](#removekey) qui supprime l’élément avec la valeur de clé donnée.

Traverser l’arbre est rendu possible avec des méthodes telles que [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext), et [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue).

Les paramètres *KTraits* et *VTraits* sont des classes de traits qui contiennent n’importe quel code supplémentaire nécessaire pour copier ou déplacer des éléments.

`CRBMap`est dérivé de [CRBTree](../../atl/reference/crbtree-class.md), qui implémente un arbre binaire à l’aide de l’algorithme Rouge-Noir. [CRBMultiMap](../../atl/reference/crbmultimap-class.md) est une variation qui permet de multiples valeurs pour chaque clé. Il est aussi `CRBTree`dérivé de , `CRBMap`et partage ainsi de nombreuses fonctionnalités avec .

Une alternative `CRBMap` aux `CRBMultiMap` deux et est offert par la classe [CAtlMap.](../../atl/reference/catlmap-class.md) Lorsque seul un petit nombre d’éléments doit être stocké, envisagez plutôt d’utiliser la classe [CSimpleMap.](../../atl/reference/csimplemap-class.md)

Pour une discussion plus complète des différentes classes de collection et de leurs caractéristiques et caractéristiques de performance, voir [atL Collection Classes](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CRBTree (en)](../../atl/reference/crbtree-class.md)

`CRBMap`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcoll.h

## <a name="crbmapcrbmap"></a><a name="crbmap"></a>CRBMap::CRBMap

Constructeur.

```
explicit CRBMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>Paramètres

*nBlockSize (en)*<br/>
Taille du bloc.

### <a name="remarks"></a>Notes

Le *paramètre nBlockSize* est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est nécessaire. De plus grandes tailles de blocs réduisent les appels aux routines d’allocation de mémoire, mais utilisent plus de ressources. La valeur par défaut allouera de l’espace pour 10 éléments à la fois.

Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les autres méthodes disponibles.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]

## <a name="crbmapcrbmap"></a><a name="dtor"></a>CRBMap::CRBMap

Destructeur.

```
~CRBMap() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les autres méthodes disponibles.

## <a name="crbmaplookup"></a><a name="lookup"></a>CRBMap::Lookup

Appelez cette méthode pour rechercher des `CRBMap` clés ou des valeurs dans l’objet.

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Spécifie la clé qui identifie l’élément à lever.

*value*<br/>
Variable qui reçoit la valeur recherchée.

### <a name="return-value"></a>Valeur de retour

La première forme de la méthode revient vrai si la clé est trouvée, autrement fausse. Les deuxième et troisième formes renvoient un pointeur à un [CPair](crbtree-class.md#cpair_class).

### <a name="remarks"></a>Notes

Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les autres méthodes disponibles.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]

## <a name="crbmapremovekey"></a><a name="removekey"></a>CRBMap::RemoveKey

Appelez cette méthode pour supprimer `CRBMap` un élément de l’objet, compte tenu de la clé.

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
La clé correspondant à la paire d’éléments que vous souhaitez supprimer.

### <a name="return-value"></a>Valeur de retour

Retourne vrai si la clé est trouvée et enlevée, fausse sur l’échec.

### <a name="remarks"></a>Notes

Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les autres méthodes disponibles.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]

## <a name="crbmapsetat"></a><a name="setat"></a>CRBMap::SetAt

Appelez cette méthode pour insérer une paire d’éléments dans la carte.

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
La valeur clé à `CRBMap` ajouter à l’objet.

*value*<br/>
La valeur à `CRBMap` ajouter à l’objet.

### <a name="return-value"></a>Valeur de retour

Retourne la position de la paire `CRBMap` d’éléments de clé/valeur dans l’objet.

### <a name="remarks"></a>Notes

`SetAt`remplace un élément existant si une clé correspondante est trouvée. Si la clé n’est pas trouvée, une nouvelle paire de clés/valeur est créée.

Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les autres méthodes disponibles.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]

## <a name="see-also"></a>Voir aussi

[Classe CRBTree](../../atl/reference/crbtree-class.md)<br/>
[Classe CAtlMap](../../atl/reference/catlmap-class.md)<br/>
[Classe CRBMultiMap](../../atl/reference/crbmultimap-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
