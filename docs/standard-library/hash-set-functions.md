---
title: '&lt;hash_set&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: d7df6b3c5dc0d0d493d17b3e9995bc4758ffd6d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370586"
---
# <a name="lthash_setgt-functions"></a>&lt;hash_set&gt;, fonctions

|||
|-|-|
|[swap](#swap)|[swap (hash_multiset)](#swap_hash_multiset)|

## <a name="swap"></a><a name="swap"></a>Swap

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Échange les éléments de deux hash_sets.

```cpp
void swap(
    hash_set <Key, Traits, Allocator>& left,
    hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Le hash_set fournissant les éléments à échanger, ou les hash_set dont les éléments doivent être échangés avec ceux de la gauche hash_set *.*

*Gauche*\
Les hash_set dont les éléments doivent être échangés avec ceux de la droite hash_set *.*

### <a name="remarks"></a>Notes

La `swap` fonction de modèle est un algorithme spécialisé dans la `left.`classe`right`de conteneurs hash_set pour exécuter l’échange [de](../standard-library/hash-set-class.md#swap)fonction de membre ( ). Il s’agit d’une instance de l’ordonnancement partiel des modèles de fonctions par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle

**template \<class T> void swap(T&, T&),**

dans la classe d’algorithme fonctionne par assignation. C’est une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide car elle peut fonctionner avec la représentation interne de la classe conteneur.

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise la version de modèle de `swap`, consultez l’exemple de code de la classe membre [hash_set::swap](../standard-library/hash-set-class.md#swap).

## <a name="swap-hash_multiset"></a><a name="swap_hash_multiset"></a>swap (hash_multiset)

> [!NOTE]
> Cette API méthode est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Échange les éléments de deux hash_multisets.

```cpp
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Le hash_multiset fournissant les éléments à échanger, ou les hash_multiset dont les éléments doivent être échangés avec ceux de la gauche hash_multiset *.*

*Gauche*\
Les hash_multiset dont les éléments doivent être échangés avec ceux de la droite hash_multiset *.*

### <a name="remarks"></a>Notes

La `swap` fonction de modèle est un algorithme spécialisé dans la `left.`classe`right`de conteneurs hash_multiset pour exécuter l’échange [de](../standard-library/hash-multiset-class.md#swap)fonction de membre ( ). Il s’agit d’une instance de l’ordonnancement partiel des modèles de fonctions par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle

**template \<class T> void swap(T&, T&),**

dans la classe d’algorithme fonctionne par assignation. C’est une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide car elle peut fonctionner avec la représentation interne de la classe conteneur.

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise la version de modèle de `swap`, consultez l’exemple de code de la classe membre [hash_multiset::swap](../standard-library/hash-multiset-class.md#swap).

## <a name="see-also"></a>Voir aussi

[<hash_set>](../standard-library/hash-set.md)
