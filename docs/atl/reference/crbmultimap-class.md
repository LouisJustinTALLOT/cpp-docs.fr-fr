---
description: 'En savoir plus sur : classe CRBMultiMap'
title: CRBMultiMap, classe
ms.date: 11/04/2016
f1_keywords:
- CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::FindFirstWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextValueWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextWithKey
- ATLCOLL/ATL::CRBMultiMap::Insert
- ATLCOLL/ATL::CRBMultiMap::RemoveKey
helpviewer_keywords:
- CRBMultiMap class
ms.assetid: 94d3ec0c-3e30-4ab7-a101-d8da4fb8add3
ms.openlocfilehash: 8dfe644521cb7ec4135c5c1f71d36371ac1706ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141022"
---
# <a name="crbmultimap-class"></a>CRBMultiMap, classe

Cette classe représente une structure de mappage qui permet à chaque clé d’être associée à plusieurs valeurs à l’aide d’une Red-Black arborescence binaire.

## <a name="syntax"></a>Syntaxe

```
template<typename K,
         typename V,
         class KTraits = CElementTraits<K>,
         class VTraits = CElementTraits<V>>
class CRBMultiMap : public CRBTree<K, V, KTraits, VTraits>
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
|[CRBMultiMap::CRBMultiMap](#crbmultimap)|Constructeur.|
|[CRBMultiMap :: ~ CRBMultiMap](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)|Appelez cette méthode pour rechercher la position du premier élément avec une clé donnée.|
|[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)|Appelez cette méthode pour obtenir la valeur associée à une clé donnée et mettre à jour la valeur de position.|
|[CRBMultiMap::GetNextWithKey](#getnextwithkey)|Appelez cette méthode pour obtenir l’élément associé à une clé donnée et mettre à jour la valeur de position.|
|[CRBMultiMap :: Insert](#insert)|Appelez cette méthode pour insérer une paire d’éléments dans la classe Map.|
|[CRBMultiMap::RemoveKey](#removekey)|Appelez cette méthode pour supprimer tous les éléments clé/valeur d’une clé donnée.|

## <a name="remarks"></a>Notes

`CRBMultiMap` fournit la prise en charge d’un tableau de mappage d’un type donné, en gérant un tableau ordonné d’éléments et de valeurs clés. Contrairement à la classe [CRBMap](../../atl/reference/crbmap-class.md) , chaque clé peut être associée à plusieurs valeurs.

Les éléments (composés d’une clé et d’une valeur) sont stockés dans une arborescence binaire à l’aide de la méthode [CRBMultiMap :: Insert](#insert) . Les éléments peuvent être supprimés à l’aide de la méthode [CRBMultiMap :: RemoveKey](#removekey) , qui supprime tous les éléments qui correspondent à la clé donnée.

Le parcours de l’arborescence est rendu possible avec des méthodes telles que [CRBTree :: GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree :: GetNext](../../atl/reference/crbtree-class.md#getnext)et [CRBTree :: GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue). L’accès aux valeurs potentiellement multiples par clé est possible à l’aide des méthodes [CRBMultiMap :: FindFirstWithKey](#findfirstwithkey), [CRBMultiMap :: GetNextValueWithKey](#getnextvaluewithkey)et [CRBMultiMap :: GetNextWithKey](#getnextwithkey) . Pour obtenir une illustration de cette procédure, consultez l’exemple de [CRBMultiMap :: CRBMultiMap](#crbmultimap) .

Les paramètres *KTraits* et *VTraits* sont des classes de caractéristiques qui contiennent tout code supplémentaire nécessaire pour copier ou déplacer des éléments.

`CRBMultiMap` est dérivée de [CRBTree](../../atl/reference/crbtree-class.md), qui implémente une arborescence binaire à l’aide de l’algorithme Red-Black. Une alternative à `CRBMultiMap` et `CRBMap` est offerte par la classe [CAtlMap](../../atl/reference/catlmap-class.md) . Lorsque seul un petit nombre d’éléments doit être stocké, envisagez d’utiliser la classe [CSimpleMap](../../atl/reference/csimplemap-class.md) à la place.

Pour une description plus complète des différentes classes de collection et de leurs fonctionnalités et caractéristiques de performances, consultez [classes de collection ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMultiMap`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="crbmultimapcrbmultimap"></a><a name="crbmultimap"></a> CRBMultiMap::CRBMultiMap

Constructeur.

```
explicit CRBMultiMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>Paramètres

*nBlockSize*<br/>
Taille du bloc.

### <a name="remarks"></a>Notes

Le paramètre *nBlockSize* est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est requis. Les tailles de bloc plus volumineuses réduisent les appels aux routines d’allocation de mémoire, mais utilisent davantage de ressources. La valeur par défaut alloue de l’espace pour 10 éléments à la fois.

Pour plus d’informations sur les autres méthodes disponibles, consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) .

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#85](../../atl/codesnippet/cpp/crbmultimap-class_1.cpp)]

## <a name="crbmultimapcrbmultimap"></a><a name="dtor"></a> CRBMultiMap :: ~ CRBMultiMap

Destructeur.

```
~CRBMultiMap() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

Pour plus d’informations sur les autres méthodes disponibles, consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) .

## <a name="crbmultimapfindfirstwithkey"></a><a name="findfirstwithkey"></a> CRBMultiMap::FindFirstWithKey

Appelez cette méthode pour rechercher la position du premier élément avec une clé donnée.

```
POSITION FindFirstWithKey(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Spécifie la clé qui identifie l’élément à rechercher.

### <a name="return-value"></a>Valeur renvoyée

Retourne la POSITION du premier élément clé/valeur si la clé est trouvée ; sinon, NULL.

### <a name="remarks"></a>Notes

Une clé dans `CRBMultiMap` peut avoir une ou plusieurs valeurs associées. Cette méthode fournira la valeur de position de la première valeur (qui peut en fait être la seule valeur) associée à cette clé particulière. La valeur de position retournée peut ensuite être utilisée avec [CRBMultiMap :: GetNextValueWithKey](#getnextvaluewithkey) ou [CRBMultiMap :: GetNextWithKey](#getnextwithkey) pour obtenir la valeur et mettre à jour la position.

Pour plus d’informations sur les autres méthodes disponibles, consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) .

### <a name="example"></a>Exemple

Consultez l’exemple de [CRBMultiMap :: CRBMultiMap](#crbmultimap).

## <a name="crbmultimapgetnextvaluewithkey"></a><a name="getnextvaluewithkey"></a> CRBMultiMap::GetNextValueWithKey

Appelez cette méthode pour obtenir la valeur associée à une clé donnée et mettre à jour la valeur de position.

```
const V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
V& GetNextValueWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Valeur de position, obtenue à l’aide d’un appel à [CRBMultiMap :: FindFirstWithKey](#findfirstwithkey) ou [CRBMultiMap :: GetNextWithKey](#getnextwithkey), ou d’un appel précédent à `GetNextValueWithKey` .

*key*<br/>
Spécifie la clé qui identifie l’élément à rechercher.

### <a name="return-value"></a>Valeur renvoyée

Retourne la paire d’éléments associée à la clé donnée.

### <a name="remarks"></a>Notes

La valeur de position est mise à jour pour pointer vers la valeur suivante associée à la clé. S’il n’existe plus aucune valeur, la valeur de position est définie sur NULL.

Pour plus d’informations sur les autres méthodes disponibles, consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) .

### <a name="example"></a>Exemple

Consultez l’exemple de [CRBMultiMap :: CRBMultiMap](#crbmultimap).

## <a name="crbmultimapgetnextwithkey"></a><a name="getnextwithkey"></a> CRBMultiMap::GetNextWithKey

Appelez cette méthode pour obtenir l’élément associé à une clé donnée et mettre à jour la valeur de position.

```
const CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) const throw();
CPair* GetNextWithKey(
    POSITION& pos,
    KINARGTYPE key) throw();
```

### <a name="parameters"></a>Paramètres

*pos*<br/>
Valeur de position, obtenue à l’aide d’un appel à [CRBMultiMap :: FindFirstWithKey](#findfirstwithkey) ou [CRBMultiMap :: GetNextValueWithKey](#getnextvaluewithkey), ou d’un appel précédent à `GetNextWithKey` .

*key*<br/>
Spécifie la clé qui identifie l’élément à rechercher.

### <a name="return-value"></a>Valeur renvoyée

Retourne l’élément de [classe CRBTree :: CPair](crbtree-class.md#cpair_class) suivant associé à la clé donnée.

### <a name="remarks"></a>Notes

La valeur de position est mise à jour pour pointer vers la valeur suivante associée à la clé. S’il n’existe plus aucune valeur, la valeur de position est définie sur NULL.

Pour plus d’informations sur les autres méthodes disponibles, consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) .

## <a name="crbmultimapinsert"></a><a name="insert"></a> CRBMultiMap :: Insert

Appelez cette méthode pour insérer une paire d’éléments dans la classe Map.

```
POSITION Insert(KINARGTYPE key, VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Valeur de clé à ajouter à l' `CRBMultiMap` objet.

*value*<br/>
Valeur à ajouter à l' `CRBMultiMap` objet, associée à la *clé*.

### <a name="return-value"></a>Valeur renvoyée

Retourne la position de la paire d’éléments clé/valeur dans l' `CRBMultiMap` objet.

### <a name="remarks"></a>Notes

Pour plus d’informations sur les autres méthodes disponibles, consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) .

### <a name="example"></a>Exemple

Consultez l’exemple de [CRBMultiMap :: CRBMultiMap](#crbmultimap).

## <a name="crbmultimapremovekey"></a><a name="removekey"></a> CRBMultiMap::RemoveKey

Appelez cette méthode pour supprimer tous les éléments clé/valeur d’une clé donnée.

```
size_t RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Spécifie la clé qui identifie le ou les éléments à supprimer.

### <a name="return-value"></a>Valeur renvoyée

Retourne le nombre de valeurs associées à la clé donnée.

### <a name="remarks"></a>Notes

`RemoveKey` supprime tous les éléments de clé/valeur qui ont une clé qui correspond à la *clé*.

Pour plus d’informations sur les autres méthodes disponibles, consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) .

### <a name="example"></a>Exemple

Consultez l’exemple de [CRBMultiMap :: CRBMultiMap](#crbmultimap).

## <a name="see-also"></a>Voir aussi

[CRBTree, classe](../../atl/reference/crbtree-class.md)<br/>
[CAtlMap, classe](../../atl/reference/catlmap-class.md)<br/>
[CRBMap, classe](../../atl/reference/crbmap-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
