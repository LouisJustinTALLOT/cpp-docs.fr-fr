---
title: '&lt;set&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- set/std::swap (map)
- set/std::swap (multiset)
ms.assetid: d1277d14-8502-46c0-b820-bcda820f9406
ms.openlocfilehash: a3a63fb86caa3485b1ee14538c3eb1f1ff72923e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78875762"
---
# <a name="ltsetgt-functions"></a>&lt;set&gt;, fonctions

## <a name="swap"></a>swap (Map)

Échange les éléments de deux classes set.

```cpp
template <class Key, class Traits, class Allocator>
void swap(set<Key, Traits, Allocator>& left, set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

\ *droit*
Jeu qui fournit les éléments à permuter, ou jeu dont les éléments doivent être échangés avec ceux du jeu de *gauche*.

\ *gauche*
Jeu dont les éléments doivent être échangés avec ceux du *droit*défini.

### <a name="remarks"></a>Notes

La fonction de modèle est un algorithme spécialisé sur la classe de conteneur définie pour exécuter la fonction membre `left.`[swap](../standard-library/set-class.md#swap)(`right`). Il s’agit d’une instance du classement partiel des modèles de fonction par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle

`template` \< **classt**> **void**( **t &** , **t &** )

dans l’algorithme de classe fonctionne par assignation et il s’agit d’une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide, car elle peut fonctionner avec la représentation interne de la classe de conteneur.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de la version de modèle de [, consultez l’exemple de code pour la classe membre ](../standard-library/set-class.md#swap)set::swap`swap`.

## <a name="swap_multiset"></a>échange (multijeu)

Échange les éléments de deux classes multiset.

```cpp
template <class Key, class Traits, class Allocator>
void swap(multiset<Key, Traits, Allocator>& left, multiset<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

\ *droit*
Multiensemble fournissant les éléments à permuter, ou le multiensemble dont les éléments doivent être échangés avec ceux du multiensemble *gauche*.

\ *gauche*
Multiensemble dont les éléments doivent être échangés avec ceux du *droit*de multiensemble.

### <a name="remarks"></a>Notes

La fonction de modèle est un algorithme spécialisé sur le multiensemble de classe de conteneur pour exécuter la fonction membre `left.`[swap](../standard-library/multiset-class.md#swap)(`right`). Il s’agit d’une instance du classement partiel des modèles de fonction par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle

`template` \< **classt**> **void**( **t &** , **t &** )

dans l’algorithme de classe fonctionne par assignation et il s’agit d’une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide, car elle peut fonctionner avec la représentation interne de la classe de conteneur.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de la version de modèle de [, consultez l’exemple de code pour la classe membre ](../standard-library/multiset-class.md#swap)multiset::swap`swap`.
