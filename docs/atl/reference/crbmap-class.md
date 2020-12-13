---
description: 'En savoir plus sur : classe CRBMap'
title: CRBMap, classe
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
ms.openlocfilehash: 55d96bfd2c7b043bdbdc4c1ee1f329c9b77b9ca9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141048"
---
# <a name="crbmap-class"></a>CRBMap, classe

Cette classe représente une structure de mappage à l’aide d’une Red-Black arborescence binaire.

## <a name="syntax"></a>Syntaxe

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CRBMap : public CRBTree<K, V, KTraits, VTraits>
```

#### <a name="parameters"></a>Paramètres

*DK*<br/>
Type d’élément clé.

*V*<br/>
Type d’élément de valeur.

*KTraits*<br/>
Code utilisé pour copier ou déplacer les éléments clés. Pour plus d’informations, consultez la [classe CElementTraits](../../atl/reference/celementtraits-class.md) .

*VTraits*<br/>
Code utilisé pour copier ou déplacer des éléments de valeur.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CRBMap::CRBMap](#crbmap)|Constructeur.|
|[CRBMap :: ~ CRBMap](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRBMap :: Lookup](#lookup)|Appelez cette méthode pour rechercher des clés ou des valeurs dans l' `CRBMap` objet.|
|[CRBMap::RemoveKey](#removekey)|Appelez cette méthode pour supprimer un élément de l' `CRBMap` objet, en fonction de la clé.|
|[CRBMap :: SetAt](#setat)|Appelez cette méthode pour insérer une paire d’éléments dans la classe Map.|

## <a name="remarks"></a>Notes

`CRBMap` fournit la prise en charge d’un tableau de mappage d’un type donné, en gérant un tableau ordonné d’éléments clés et leurs valeurs associées. Chaque clé ne peut avoir qu’une seule valeur associée. Les éléments (composés d’une clé et d’une valeur) sont stockés dans une arborescence binaire à l’aide de la méthode [CRBMap :: setat](#setat) . Les éléments peuvent être supprimés à l’aide de la méthode [CRBMap :: RemoveKey](#removekey) , qui supprime l’élément avec la valeur de clé donnée.

Le parcours de l’arborescence est rendu possible avec des méthodes telles que [CRBTree :: GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree :: GetNext](../../atl/reference/crbtree-class.md#getnext)et [CRBTree :: GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue).

Les paramètres *KTraits* et *VTraits* sont des classes de caractéristiques qui contiennent tout code supplémentaire nécessaire pour copier ou déplacer des éléments.

`CRBMap` est dérivée de [CRBTree](../../atl/reference/crbtree-class.md), qui implémente une arborescence binaire à l’aide de l’algorithme Red-Black. [CRBMultiMap](../../atl/reference/crbmultimap-class.md) est une variante qui autorise plusieurs valeurs pour chaque clé. Il est également dérivé de `CRBTree` et partage donc de nombreuses fonctionnalités avec `CRBMap` .

Une alternative à `CRBMap` et `CRBMultiMap` est proposée par la classe [CAtlMap](../../atl/reference/catlmap-class.md) . Lorsque seul un petit nombre d’éléments doit être stocké, envisagez d’utiliser la classe [CSimpleMap](../../atl/reference/csimplemap-class.md) à la place.

Pour une description plus complète des différentes classes de collection et de leurs fonctionnalités et caractéristiques de performances, consultez [classes de collection ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMap`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="crbmapcrbmap"></a><a name="crbmap"></a> CRBMap::CRBMap

Constructeur.

```
explicit CRBMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>Paramètres

*nBlockSize*<br/>
Taille du bloc.

### <a name="remarks"></a>Notes

Le paramètre *nBlockSize* est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est requis. Les tailles de bloc plus volumineuses réduisent les appels aux routines d’allocation de mémoire, mais utilisent davantage de ressources. La valeur par défaut alloue de l’espace pour 10 éléments à la fois.

Pour plus d’informations sur les autres méthodes disponibles, consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]

## <a name="crbmapcrbmap"></a><a name="dtor"></a> CRBMap :: ~ CRBMap

Destructeur.

```
~CRBMap() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

Pour plus d’informations sur les autres méthodes disponibles, consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) .

## <a name="crbmaplookup"></a><a name="lookup"></a> CRBMap :: Lookup

Appelez cette méthode pour rechercher des clés ou des valeurs dans l' `CRBMap` objet.

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Spécifie la clé qui identifie l’élément à rechercher.

*value*<br/>
Variable qui reçoit la valeur recherchée.

### <a name="return-value"></a>Valeur renvoyée

La première forme de la méthode retourne la valeur true si la clé est trouvée ; sinon, false. Les deuxième et troisième formes retournent un pointeur vers un [CPair](crbtree-class.md#cpair_class).

### <a name="remarks"></a>Notes

Pour plus d’informations sur les autres méthodes disponibles, consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]

## <a name="crbmapremovekey"></a><a name="removekey"></a> CRBMap::RemoveKey

Appelez cette méthode pour supprimer un élément de l' `CRBMap` objet, en fonction de la clé.

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé correspondant à la paire d’éléments que vous souhaitez supprimer.

### <a name="return-value"></a>Valeur renvoyée

Retourne la valeur true si la clé est trouvée et supprimée, false en cas d’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les autres méthodes disponibles, consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]

## <a name="crbmapsetat"></a><a name="setat"></a> CRBMap :: SetAt

Appelez cette méthode pour insérer une paire d’éléments dans la classe Map.

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à ajouter à l' `CRBMap` objet.

*value*<br/>
Valeur à ajouter à l' `CRBMap` objet.

### <a name="return-value"></a>Valeur renvoyée

Retourne la position de la paire d’éléments clé/valeur dans l' `CRBMap` objet.

### <a name="remarks"></a>Notes

`SetAt` remplace un élément existant si une clé correspondante est trouvée. Si la clé est introuvable, une nouvelle paire clé/valeur est créée.

Pour plus d’informations sur les autres méthodes disponibles, consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]

## <a name="see-also"></a>Voir aussi

[CRBTree, classe](../../atl/reference/crbtree-class.md)<br/>
[CAtlMap, classe](../../atl/reference/catlmap-class.md)<br/>
[CRBMultiMap, classe](../../atl/reference/crbmultimap-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
