---
title: CRBMultiMap, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::CRBMultiMap
- ATLCOLL/ATL::CRBMultiMap::FindFirstWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextValueWithKey
- ATLCOLL/ATL::CRBMultiMap::GetNextWithKey
- ATLCOLL/ATL::CRBMultiMap::Insert
- ATLCOLL/ATL::CRBMultiMap::RemoveKey
dev_langs:
- C++
helpviewer_keywords:
- CRBMultiMap class
ms.assetid: 94d3ec0c-3e30-4ab7-a101-d8da4fb8add3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae9a83ff8cc8e4909e23e7751e0c82da690a0c21
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093816"
---
# <a name="crbmultimap-class"></a>CRBMultiMap, classe

Cette classe représente une structure de mappage qui permet à que chaque clé peut être associé à plusieurs valeurs, à l’aide d’une arborescence binaire rouge-noire.

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

*KTraits*<br/>
Le code utilisé pour copier ou déplacer les éléments clés. Consultez [celementtraits, classe](../../atl/reference/celementtraits-class.md) pour plus d’informations.

*VTraits*<br/>
Le code utilisé pour copier ou déplacer des éléments de valeur.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CRBMultiMap::CRBMultiMap](#crbmultimap)|Constructeur.|
|[CRBMultiMap :: ~ CRBMultiMap](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRBMultiMap::FindFirstWithKey](#findfirstwithkey)|Appelez cette méthode pour trouver la position du premier élément avec une clé donnée.|
|[CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey)|Appelez cette méthode pour obtenir la valeur associée à une clé donnée et mettre à jour la valeur de position.|
|[CRBMultiMap::GetNextWithKey](#getnextwithkey)|Appelez cette méthode pour obtenir l’élément associé à une clé donnée et mettre à jour la valeur de position.|
|[CRBMultiMap::Insert](#insert)|Appelez cette méthode pour insérer une paire de l’élément dans la classe map.|
|[CRBMultiMap::RemoveKey](#removekey)|Appelez cette méthode pour supprimer tous les éléments de clé/valeur pour une clé donnée.|

## <a name="remarks"></a>Notes

`CRBMultiMap` prend en charge un tableau de mappage d’un type donné, la gestion d’un tableau ordonné d’éléments clés et valeurs. Contrairement à la [CRBMap](../../atl/reference/crbmap-class.md) (classe), chaque clé peut être associé à plusieurs valeurs.

Éléments (composé d’une clé et une valeur) sont stockés dans une arborescence binaire à l’aide de la structure du [CRBMultiMap::Insert](#insert) (méthode). Éléments peuvent être supprimés à l’aide de la [CRBMultiMap::RemoveKey](#removekey) (méthode), ce qui supprime tous les éléments qui correspondent à la clé donnée.

Parcourt l’arborescence est rendue possible avec des méthodes telles que [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext), et [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue). L’accès à la potentiellement plusieurs valeurs par clé possible utilise le [CRBMultiMap::FindFirstWithKey](#findfirstwithkey), [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey), et [CRBMultiMap::GetNextWithKey ](#getnextwithkey) méthodes. Consultez l’exemple de [CRBMultiMap::CRBMultiMap](#crbmultimap) pour obtenir une illustration de ce dans la pratique.

Le *KTraits* et *VTraits* paramètres sont des classes de traits qui contiennent tout code supplémentaire nécessaire pour copier ou déplacer des éléments.

`CRBMultiMap` est dérivé de [CRBTree](../../atl/reference/crbtree-class.md), qui implémente un arbre binaire à l’aide de l’algorithme rouge-noire. Une alternative à `CRBMultiMap` et `CRBMap` est proposé par le [CAtlMap](../../atl/reference/catlmap-class.md) classe. Lorsque seulement un petit nombre d’éléments doit être stockées, envisagez d’utiliser le [CSimpleMap](../../atl/reference/csimplemap-class.md) classe à la place.

Pour obtenir une description plus complète de diverses classes de collection et leurs fonctions et les caractéristiques de performances, consultez [ATL, Classes de Collection](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMultiMap`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcoll.h

##  <a name="crbmultimap"></a>  CRBMultiMap::CRBMultiMap

Constructeur.

```
explicit CRBMultiMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>Paramètres

*nBlockSize*<br/>
La taille du bloc.

### <a name="remarks"></a>Notes

Le *nBlockSize* paramètre est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est requis. Tailles de bloc supérieures réduisent les appels aux routines d’allocation de mémoire, mais utilisent davantage de ressources. La valeur par défaut alloue de l’espace de 10 éléments à la fois.

Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les autres méthodes disponibles.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#85](../../atl/codesnippet/cpp/crbmultimap-class_1.cpp)]

##  <a name="dtor"></a>  CRBMultiMap :: ~ CRBMultiMap

Destructeur.

```
~CRBMultiMap() throw();
```

### <a name="remarks"></a>Notes

Libère toutes les ressources allouées.

Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les autres méthodes disponibles.

##  <a name="findfirstwithkey"></a>  CRBMultiMap::FindFirstWithKey

Appelez cette méthode pour trouver la position du premier élément avec une clé donnée.

```
POSITION FindFirstWithKey(KINARGTYPE key) const throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Spécifie la clé qui identifie l’élément à rechercher.

### <a name="return-value"></a>Valeur de retour

Retourne la POSITION du premier élément de clé/valeur si la clé est trouvée, NULL sinon.

### <a name="remarks"></a>Notes

Une clé dans le `CRBMultiMap` peut avoir une ou plusieurs valeurs associées. Cette méthode fournit la valeur de position de la première valeur (qui peut être en fait, la seule valeur) associée à cette clé particulière. La valeur de position retournée peut ensuite être utilisée avec [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey) ou [CRBMultiMap::GetNextWithKey](#getnextwithkey) pour obtenir la valeur et de mettre à jour la position.

Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les autres méthodes disponibles.

### <a name="example"></a>Exemple

Consultez l’exemple de [CRBMultiMap::CRBMultiMap](#crbmultimap).

##  <a name="getnextvaluewithkey"></a>  CRBMultiMap::GetNextValueWithKey

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

*points de vente*<br/>
La valeur de position, obtenue avec soit un appel à [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) ou [CRBMultiMap::GetNextWithKey](#getnextwithkey), ou un appel précédent à `GetNextValueWithKey`.

*key*<br/>
Spécifie la clé qui identifie l’élément à rechercher.

### <a name="return-value"></a>Valeur de retour

Retourne la paire de l’élément associée à la clé donnée.

### <a name="remarks"></a>Notes

La valeur de position est mis à jour pour pointer vers la valeur suivante est associée à la clé. Si aucune valeur n’existe pas, la valeur de position est définie sur NULL.

Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les autres méthodes disponibles.

### <a name="example"></a>Exemple

Consultez l’exemple de [CRBMultiMap::CRBMultiMap](#crbmultimap).

##  <a name="getnextwithkey"></a>  CRBMultiMap::GetNextWithKey

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

*points de vente*<br/>
La valeur de position, obtenue avec soit un appel à [CRBMultiMap::FindFirstWithKey](#findfirstwithkey) ou [CRBMultiMap::GetNextValueWithKey](#getnextvaluewithkey), ou un appel précédent à `GetNextWithKey`.

*key*<br/>
Spécifie la clé qui identifie l’élément à rechercher.

### <a name="return-value"></a>Valeur de retour

Renvoie la prochaine [CRBTree::CPair classe](crbtree-class.md#cpair_class) élément associé à la clé donnée.

### <a name="remarks"></a>Notes

La valeur de position est mis à jour pour pointer vers la valeur suivante est associée à la clé. Si aucune valeur n’existe pas, la valeur de position est définie sur NULL.

Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les autres méthodes disponibles.

##  <a name="insert"></a>  CRBMultiMap::Insert

Appelez cette méthode pour insérer une paire de l’élément dans la classe map.

```
POSITION Insert(KINARGTYPE key, VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>Paramètres

*key*<br/>
La valeur de clé à ajouter à la `CRBMultiMap` objet.

*valeur*<br/>
La valeur à ajouter à la `CRBMultiMap` est associé, *clé*.

### <a name="return-value"></a>Valeur de retour

Retourne la position de la paire d’élément de clé/valeur dans la `CRBMultiMap` objet.

### <a name="remarks"></a>Notes

Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les autres méthodes disponibles.

### <a name="example"></a>Exemple

Consultez l’exemple de [CRBMultiMap::CRBMultiMap](#crbmultimap).

##  <a name="removekey"></a>  CRBMultiMap::RemoveKey

Appelez cette méthode pour supprimer tous les éléments de clé/valeur pour une clé donnée.

```
size_t RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Spécifie la clé qui identifie l’ou les éléments à supprimer.

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de valeurs associées à la clé donnée.

### <a name="remarks"></a>Notes

`RemoveKey` Supprime tous les éléments de clé/valeur comportant une clé qui correspond à *clé*.

Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les autres méthodes disponibles.

### <a name="example"></a>Exemple

Consultez l’exemple de [CRBMultiMap::CRBMultiMap](#crbmultimap).

## <a name="see-also"></a>Voir aussi

[CRBTree, classe](../../atl/reference/crbtree-class.md)<br/>
[CAtlMap, classe](../../atl/reference/catlmap-class.md)<br/>
[CRBMap, classe](../../atl/reference/crbmap-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
