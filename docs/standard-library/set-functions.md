---
title: '&lt;set&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- set/std::swap (map)
- set/std::swap (multiset)
ms.assetid: d1277d14-8502-46c0-b820-bcda820f9406
ms.openlocfilehash: a3a63fb86caa3485b1ee14538c3eb1f1ff72923e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246415"
---
# <a name="ltsetgt-functions"></a>&lt;set&gt;, fonctions

## <a name="swap"></a> swap (map)

Échange les éléments de deux classes set.

```cpp
template <class Key, class Traits, class Allocator>
void swap(set<Key, Traits, Allocator>& left, set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Le jeu qui fournit les éléments à échanger ou set dont les éléments doivent être échangés avec ceux du jeu de *gauche*.

*Gauche*\
Le jeu dont les éléments doivent être échangés avec ceux du set *droit*.

### <a name="remarks"></a>Notes

La fonction de modèle est un algorithme spécialisé sur la classe de conteneur set pour exécuter la fonction membre `left.` [échange](../standard-library/set-class.md#swap)(`right`). Il s’agit d’une instance du classement partiel des modèles de fonction par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle

`template` \< **classT**> **void swap**( **T&** , **T&** )

dans la classe d’algorithme fonctionne par assignation. C’est une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide, car elle peut fonctionner avec la représentation interne de la classe conteneur.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de la version de modèle de `swap`, consultez l’exemple de code pour la classe membre [set::swap](../standard-library/set-class.md#swap).

## <a name="swap_multiset"></a> swap (multiset)

Échange les éléments de deux multisets.

```cpp
template <class Key, class Traits, class Allocator>
void swap(multiset<Key, Traits, Allocator>& left, multiset<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
La classe multiset qui fournit les éléments à échanger ou multiset dont les éléments doivent être échangés avec ceux du multiset *gauche*.

*Gauche*\
Multiset dont les éléments doivent être échangés avec ceux du multiset *droit*.

### <a name="remarks"></a>Notes

La fonction de modèle est un algorithme spécialisé sur la classe de conteneur multiset pour exécuter la fonction membre `left.` [échange](../standard-library/multiset-class.md#swap)(`right`). Il s’agit d’une instance du classement partiel des modèles de fonction par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle

`template` \< **classT**> **void swap**( **T&** , **T&** )

dans la classe d’algorithme fonctionne par assignation. C’est une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide, car elle peut fonctionner avec la représentation interne de la classe conteneur.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de la version de modèle de `swap`, consultez l’exemple de code pour la classe membre [multiset::swap](../standard-library/multiset-class.md#swap).
