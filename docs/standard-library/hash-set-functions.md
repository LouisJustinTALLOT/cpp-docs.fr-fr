---
description: 'En savoir plus sur les fonctions suivantes : &lt; hash_set &gt;'
title: '&lt;hash_set&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: 7040325f3af26052306b1ebd90f1919d96dcbf19
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231794"
---
# <a name="lthash_setgt-functions"></a>&lt;hash_set&gt;, fonctions

[échange](#swap)\
[swap (hash_multiset)](#swap_hash_multiset)

## <a name="swap"></a><a name="swap"></a> échange

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Échange les éléments de deux hash_sets.

```cpp
void swap(
    hash_set <Key, Traits, Allocator>& left,
    hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Hash_set qui fournit les éléments à permuter, ou le hash_set dont les éléments doivent être échangés avec ceux du hash_set *gauche*.

*gauche*\
Hash_set dont les éléments doivent être échangés avec ceux du hash_set *droit*.

### <a name="remarks"></a>Notes

La `swap` fonction de modèle est un algorithme spécialisé sur la classe de conteneur hash_set pour exécuter la fonction membre `left.` [swap](../standard-library/hash-set-class.md#swap)( `right` ). Il s’agit d’une instance de l’ordonnancement partiel des modèles de fonctions par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle

**template \<class T> void swap (t&, t&),**

dans la classe d’algorithme fonctionne par assignation. C’est une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide car elle peut fonctionner avec la représentation interne de la classe conteneur.

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise la version de modèle de `swap`, consultez l’exemple de code de la classe membre [hash_set::swap](../standard-library/hash-set-class.md#swap).

## <a name="swap-hash_multiset"></a><a name="swap_hash_multiset"></a> échange (hash_multiset)

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Échange les éléments de deux hash_multisets.

```cpp
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Hash_multiset qui fournit les éléments à permuter, ou le hash_multiset dont les éléments doivent être échangés avec ceux du hash_multiset *gauche*.

*gauche*\
Hash_multiset dont les éléments doivent être échangés avec ceux du hash_multiset *droit*.

### <a name="remarks"></a>Notes

La `swap` fonction de modèle est un algorithme spécialisé sur la classe de conteneur hash_multiset pour exécuter la fonction membre `left.` [swap](../standard-library/hash-multiset-class.md#swap)( `right` ). Il s’agit d’une instance de l’ordonnancement partiel des modèles de fonctions par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle

**template \<class T> void swap (t&, t&),**

dans la classe d’algorithme fonctionne par assignation. C’est une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide car elle peut fonctionner avec la représentation interne de la classe conteneur.

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise la version de modèle de `swap`, consultez l’exemple de code de la classe membre [hash_multiset::swap](../standard-library/hash-multiset-class.md#swap).

## <a name="see-also"></a>Voir aussi

[<hash_set>](../standard-library/hash-set.md)
