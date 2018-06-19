---
title: '&lt;hash_set&gt;, fonctions | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- hash_set/std::swap
- hash_set/std::swap (hash_multiset)
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
ms.openlocfilehash: 083d928198d8d83d8a56d8a74a6204e94c86aa67
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846283"
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

`right` La classe hash_set qui fournit les éléments à permuter, ou la classe hash_set dont les éléments doivent être échangés avec ceux de la classe hash_set `left`.

`left` La classe hash_set dont les éléments doivent être échangés avec ceux de la classe hash_set `right`.

### <a name="remarks"></a>Notes

La fonction de modèle `swap` est un algorithme spécialisé sur la classe de conteneur hash_set pour exécuter la fonction membre `left.`[swap](../standard-library/hash-set-class.md#swap)( `right`). Il s’agit d’une instance du classement partiel des modèles de fonction par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle

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

`right` Le hash_multiset qui fournit les éléments à permuter, ou le hash_multiset dont les éléments doivent être échangés avec ceux du hash_multiset `left`.

`left` Le hash_multiset dont les éléments doivent être échangés avec ceux du hash_multiset `right`.

### <a name="remarks"></a>Notes

La fonction de modèle `swap` est un algorithme spécialisé sur la classe de conteneur hash_multiset pour exécuter la fonction membre `left.`[swap](../standard-library/hash-multiset-class.md#swap)( `right`). Il s’agit d’une instance du classement partiel des modèles de fonction par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle

**template \<class T> void swap(T&, T&),**

dans l’algorithme de classe fonctionne par assignation et il s’agit d’une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide, car elle peut fonctionner avec la représentation interne de la classe conteneur.

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise la version de modèle de `swap`, consultez l’exemple de code de la classe membre [hash_multiset::swap](../standard-library/hash-multiset-class.md#swap).

## <a name="see-also"></a>Voir aussi

[<hash_set>](../standard-library/hash-set.md)<br/>
