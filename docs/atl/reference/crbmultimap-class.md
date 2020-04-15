---
title: Classe CRBMultiMap
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
ms.openlocfilehash: 1e36bc267b3a539d2d1d4bf370b9cdc33828c760
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331424"
---
# <a name="crbmultimap-class"></a>Classe CRBMultiMap

Cette classe représente une structure de cartographie qui permet à chaque clé peut être associée à plus d’une valeur, à l’aide d’un arbre binaire Rouge-Noir.

## <a name="syntax"></a>Syntaxe

```
template<typename K,
         typename V,
         class KTraits = CElementTraits<K>,
         class VTraits = CElementTraits<V>>
class CRBMultiMap : public CRBTree<K, V, KTraits, VTraits>
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
|[CRBMultiMap::CRBMultiMap](#crbmultimap)|Constructeur.|
|[CRBMultiMap::CRBMultiMap](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)|Appelez cette méthode pour trouver la position du premier élément avec une clé donnée.|
|[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)|Appelez cette méthode pour obtenir la valeur associée à une clé donnée, et mettre à jour la valeur de position.|
|[CRBMultiMap::GetNextWithKey](#getnextwithkey)|Appelez cette méthode pour obtenir l’élément associé à une clé donnée, et mettre à jour la valeur de position.|
|[CRBMultiMap::Insérer](#insert)|Appelez cette méthode pour insérer une paire d’éléments dans la carte.|
|[CRBMultiMap::RemoveKey](#removekey)|Appelez cette méthode pour supprimer tous les éléments clés/valeur pour une clé donnée.|

## <a name="remarks"></a>Notes

`CRBMultiMap`fournit un soutien pour un tableau de cartographie de n’importe quel type donné, la gestion d’un tableau ordonné d’éléments clés et de valeurs. Contrairement à la classe [CRBMap,](../../atl/reference/crbmap-class.md) chaque clé peut être associée à plus d’une valeur.

Les éléments (composés d’une clé et d’une valeur) sont stockés dans une structure d’arbre binaire, à l’aide de la [méthode CRBMultiMap::Insert](#insert) method. Les éléments peuvent être supprimés à l’aide de la méthode [CRBMultiMap::RemoveKey,](#removekey) qui supprime tous les éléments qui correspondent à la clé donnée.

Traverser l’arbre est rendu possible avec des méthodes telles que [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext), et [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue). L’accès aux valeurs potentiellement multiples par clé est possible à l’aide du [CRBMultiMap::FindFirstWithKey](#findfirstwithkey), [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey), et [CRBMultiMap::GetNextWithKey](#getnextwithkey) méthodes. Voir l’exemple pour [CRBMultiMap::CRBMultiMap](#crbmultimap) pour une illustration de cela dans la pratique.

Les paramètres *KTraits* et *VTraits* sont des classes de traits qui contiennent n’importe quel code supplémentaire nécessaire pour copier ou déplacer des éléments.

`CRBMultiMap`est dérivé de [CRBTree](../../atl/reference/crbtree-class.md), qui implémente un arbre binaire à l’aide de l’algorithme Rouge-Noir. Une alternative `CRBMultiMap` `CRBMap` à et est offerte par la classe [CAtlMap.](../../atl/reference/catlmap-class.md) Lorsque seul un petit nombre d’éléments doit être stocké, envisagez plutôt d’utiliser la classe [CSimpleMap.](../../atl/reference/csimplemap-class.md)

Pour une discussion plus complète des différentes classes de collection et de leurs caractéristiques et caractéristiques de performance, voir [atL Collection Classes](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CRBTree (en)](../../atl/reference/crbtree-class.md)

`CRBMultiMap`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcoll.h

## <a name="crbmultimapcrbmultimap"></a><a name="crbmultimap"></a>CRBMultiMap::CRBMultiMap

Constructeur.

```
explicit CRBMultiMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>Paramètres

*nBlockSize (en)*<br/>
Taille du bloc.

### <a name="remarks"></a>Notes

Le *paramètre nBlockSize* est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est nécessaire. De plus grandes tailles de blocs réduisent les appels aux routines d’allocation de mémoire, mais utilisent plus de ressources. La valeur par défaut allouera de l’espace pour 10 éléments à la fois.

Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les autres méthodes disponibles.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#85](../../atl/codesnippet/cpp/crbmultimap-class_1.cpp)]

## <a name="crbmultimapcrbmultimap"></a><a name="dtor"></a>CRBMultiMap::CRBMultiMap

Destructeur.

```
~CRBMultiMap() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les autres méthodes disponibles.

## <a name="crbmultimapfindfirstwithkey"></a><a name="findfirstwithkey"></a>CRBMultiMap::FindFirstWithKey

Appelez cette méthode pour trouver la position du premier élément avec une clé donnée.

```
POSITION FindFirstWithKey(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Spécifie la clé qui identifie l’élément à trouver.

### <a name="return-value"></a>Valeur de retour

Retourne la POSITION du premier élément clé/valeur si la clé est trouvée, NULL autrement.

### <a name="remarks"></a>Notes

Une clé `CRBMultiMap` dans le peut avoir une ou plusieurs valeurs associées. Cette méthode fournira la valeur de position de la première valeur (qui peut, en fait, être la seule valeur) associée à cette clé particulière. La valeur de position retournée peut ensuite être utilisée avec [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey) ou [CRBMultiMap::GetNextWithKey](#getnextwithkey) pour obtenir la valeur et mettre à jour la position.

Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les autres méthodes disponibles.

### <a name="example"></a>Exemple

Voir l’exemple pour [CRBMultiMap::CRBMultiMap](#crbmultimap).

## <a name="crbmultimapgetnextvaluewithkey"></a><a name="getnextvaluewithkey"></a>CRBMultiMap::GetNextValueWithKey

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

*Pos*<br/>
La valeur de position, obtenue soit avec un appel à [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) ou [CRBMultiMap::GetNextWithKey](#getnextwithkey), ou un appel précédent à `GetNextValueWithKey`.

*key*<br/>
Spécifie la clé qui identifie l’élément à trouver.

### <a name="return-value"></a>Valeur de retour

Retourne la paire d’éléments associée à la clé donnée.

### <a name="remarks"></a>Notes

La valeur de position est mise à jour pour indiquer la valeur suivante associée à la clé. S’il n’existe plus de valeurs, la valeur de position est définie à NULL.

Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les autres méthodes disponibles.

### <a name="example"></a>Exemple

Voir l’exemple pour [CRBMultiMap::CRBMultiMap](#crbmultimap).

## <a name="crbmultimapgetnextwithkey"></a><a name="getnextwithkey"></a>CRBMultiMap::GetNextWithKey

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

*Pos*<br/>
La valeur de position, obtenue soit avec un appel à [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) ou [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey), ou un appel précédent à `GetNextWithKey`.

*key*<br/>
Spécifie la clé qui identifie l’élément à trouver.

### <a name="return-value"></a>Valeur de retour

Retourne le prochain [CRBTree::CPair Class](crbtree-class.md#cpair_class) élément associé à la clé donnée.

### <a name="remarks"></a>Notes

La valeur de position est mise à jour pour indiquer la valeur suivante associée à la clé. S’il n’existe plus de valeurs, la valeur de position est définie à NULL.

Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les autres méthodes disponibles.

## <a name="crbmultimapinsert"></a><a name="insert"></a>CRBMultiMap::Insérer

Appelez cette méthode pour insérer une paire d’éléments dans la carte.

```
POSITION Insert(KINARGTYPE key, VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
La valeur clé à `CRBMultiMap` ajouter à l’objet.

*value*<br/>
La valeur à `CRBMultiMap` ajouter à l’objet, associé à *la clé*.

### <a name="return-value"></a>Valeur de retour

Retourne la position de la paire `CRBMultiMap` d’éléments de clé/valeur dans l’objet.

### <a name="remarks"></a>Notes

Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les autres méthodes disponibles.

### <a name="example"></a>Exemple

Voir l’exemple pour [CRBMultiMap::CRBMultiMap](#crbmultimap).

## <a name="crbmultimapremovekey"></a><a name="removekey"></a>CRBMultiMap::RemoveKey

Appelez cette méthode pour supprimer tous les éléments clés/valeur pour une clé donnée.

```
size_t RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Spécifie la clé qui identifie l’élément (s) à supprimer.

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de valeurs associées à la clé donnée.

### <a name="remarks"></a>Notes

`RemoveKey`supprime tous les éléments clés/valeurs qui ont une clé qui correspond à *la clé*.

Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les autres méthodes disponibles.

### <a name="example"></a>Exemple

Voir l’exemple pour [CRBMultiMap::CRBMultiMap](#crbmultimap).

## <a name="see-also"></a>Voir aussi

[Classe CRBTree](../../atl/reference/crbtree-class.md)<br/>
[Classe CAtlMap](../../atl/reference/catlmap-class.md)<br/>
[Classe CRBMap](../../atl/reference/crbmap-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
