---
title: '&lt;hash_map&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
ms.openlocfilehash: 7cb2e46f19bd30e3eb313cde867c6a055cb8bca5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370614"
---
# <a name="lthash_mapgt-functions"></a>&lt;hash_map&gt;, fonctions

|||
|-|-|
|[swap](#swap)|[swap (hash_map)](#swap_hash_map)|

## <a name="swap-hash_map"></a><a name="swap_hash_map"></a>swap (hash_map)

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Échange les éléments de deux hash_maps.

```cpp
void swap(
    hash_map <Key, Type, Traits, Alloctor>& left,
    hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Les hash_map dont les éléments doivent être échangés avec ceux de la carte *à gauche*.

*Gauche*\
Les hash_map dont les éléments doivent être échangés avec ceux de la carte *droite*.

### <a name="remarks"></a>Notes

La fonction de modèle est un algorithme spécialisé sur la classe de conteneur hash_map pour exécuter la fonction membre `left.`[swap](../standard-library/basic-ios-class.md#swap)*(right*). Il s’agit d’une instance de l’ordonnancement partiel des modèles de fonctions par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle, **template \<class T> void swap(T&, T&)**, dans le fichier d’en-tête d’algorithme fonctionne par assignation et est une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide car elle peut fonctionner avec la représentation interne de la classe conteneur.

## <a name="swap"></a><a name="swap"></a>Swap

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_multimap Class](../standard-library/unordered-multimap-class.md).

Échange les éléments de deux hash_multimaps.

```cpp
void swap(
    hash_multimap <Key, Type, Traits, Alloctor>& left,
    hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Les hash_multimap dont les éléments doivent être échangés avec ceux de la carte *à gauche*.

*Gauche*\
Les hash_multimap dont les éléments doivent être échangés avec ceux de la carte *droite*.

### <a name="remarks"></a>Notes

La fonction de modèle est un algorithme spécialisé sur la classe de conteneur hash_multimap pour exécuter la fonction membre `left.`[swap](../standard-library/hash-multimap-class.md#swap)*(right*`)`. Il s’agit d’une instance de l’ordonnancement partiel des modèles de fonctions par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle, **template \<class T> void swap(T&, T&)**, dans le fichier d’en-tête d’algorithme fonctionne par assignation et est une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide car elle peut fonctionner avec la représentation interne de la classe conteneur.

## <a name="see-also"></a>Voir aussi

[<>hash_map](../standard-library/hash-map.md)
