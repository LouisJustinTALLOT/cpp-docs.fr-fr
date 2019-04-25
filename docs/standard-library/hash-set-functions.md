---
title: '&lt;hash_set&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: 05a7ffd1e3bf02a88fe6a6cce841a440550c1057
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159130"
---
# <a name="lthashsetgt-functions"></a>&lt;hash_set&gt;, fonctions

|||
|-|-|
|[swap](#swap)|[swap (hash_multiset)](#swap_hash_multiset)|

## <a name="swap"></a>  swap

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Échange les éléments de deux hash_sets.

```cpp
void swap(
    hash_set <Key, Traits, Allocator>& left,
    hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*right*<br/>
La classe hash_set qui fournit les éléments à échanger ou hash_set dont les éléments doivent être échangés avec ceux du hash_set *gauche*.

*left*<br/>
Hash_set dont les éléments doivent être échangés avec ceux du hash_set *droit*.

### <a name="remarks"></a>Notes

Le `swap` fonction de modèle est un algorithme spécialisé sur la classe conteneur hash_set pour exécuter la fonction membre `left.` [échange](../standard-library/hash-set-class.md#swap)(`right`). Il s’agit d’une instance du classement partiel des modèles de fonction par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle

**template \<class T> void swap(T&, T&),**

dans l’algorithme de classe fonctionne par assignation et il s’agit d’une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide, car elle peut fonctionner avec la représentation interne de la classe conteneur.

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise la version de modèle de `swap`, consultez l’exemple de code de la classe membre [hash_set::swap](../standard-library/hash-set-class.md#swap).

## <a name="swap_hash_multiset"></a>  swap (hash_multiset)

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_set, classe](../standard-library/unordered-set-class.md).

Échange les éléments de deux hash_multisets.

```cpp
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Le hash_multiset qui fournit les éléments à échanger, ou le hash_multiset dont les éléments doivent être échangés avec ceux du hash_multiset *gauche*.

*left*<br/>
Le hash_multiset dont les éléments doivent être échangés avec ceux du hash_multiset *droit*.

### <a name="remarks"></a>Notes

Le `swap` fonction de modèle est un algorithme spécialisé sur la classe conteneur hash_multiset pour exécuter la fonction membre `left.` [échange](../standard-library/hash-multiset-class.md#swap)(`right`). Il s’agit d’une instance du classement partiel des modèles de fonction par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle

**template \<class T> void swap(T&, T&),**

dans l’algorithme de classe fonctionne par assignation et il s’agit d’une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide, car elle peut fonctionner avec la représentation interne de la classe conteneur.

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise la version de modèle de `swap`, consultez l’exemple de code de la classe membre [hash_multiset::swap](../standard-library/hash-multiset-class.md#swap).

## <a name="see-also"></a>Voir aussi

[<hash_set>](../standard-library/hash-set.md)<br/>
