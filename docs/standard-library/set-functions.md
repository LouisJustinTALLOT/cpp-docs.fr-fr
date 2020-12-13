---
description: 'En savoir plus sur : &lt; définir des &gt; fonctions'
title: '&lt;set&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- set/std::swap (map)
- set/std::swap (multiset)
ms.assetid: d1277d14-8502-46c0-b820-bcda820f9406
ms.openlocfilehash: 14f8eac3f725f88d98cdba133dace06993e5c089
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154134"
---
# <a name="ltsetgt-functions"></a>&lt;set&gt;, fonctions

## <a name="swap-map"></a><a name="swap"></a> swap (Map)

Échange les éléments de deux classes set.

```cpp
template <class Key, class Traits, class Allocator>
void swap(set<Key, Traits, Allocator>& left, set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Jeu qui fournit les éléments à permuter, ou jeu dont les éléments doivent être échangés avec ceux du jeu de *gauche*.

*gauche*\
Jeu dont les éléments doivent être échangés avec ceux du *droit* défini.

### <a name="remarks"></a>Notes

La fonction de modèle est un algorithme spécialisé sur la classe de conteneur définie pour exécuter la fonction membre `left.` [swap](../standard-library/set-class.md#swap)( `right` ). Il s’agit d’une instance de l’ordonnancement partiel des modèles de fonctions par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle

`template`\< **classT**> **void void**( **t&**, **t&**)

dans la classe d’algorithme fonctionne par assignation. C’est une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide car elle peut fonctionner avec la représentation interne de la classe conteneur.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de la version de modèle de `swap`, consultez l’exemple de code pour la classe membre [set::swap](../standard-library/set-class.md#swap).

## <a name="swap-multiset"></a><a name="swap_multiset"></a> échange (multijeu)

Échange les éléments de deux multisets.

```cpp
template <class Key, class Traits, class Allocator>
void swap(multiset<Key, Traits, Allocator>& left, multiset<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Multiensemble fournissant les éléments à permuter, ou le multiensemble dont les éléments doivent être échangés avec ceux du multiensemble *gauche*.

*gauche*\
Multiensemble dont les éléments doivent être échangés avec ceux du *droit* de multiensemble.

### <a name="remarks"></a>Notes

La fonction de modèle est un algorithme spécialisé sur le multiensemble de classe de conteneur pour exécuter la fonction membre `left.` [swap](../standard-library/multiset-class.md#swap)( `right` ). Il s’agit d’une instance de l’ordonnancement partiel des modèles de fonctions par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle

`template`\< **classT**> **void void**( **t&**, **t&**)

dans la classe d’algorithme fonctionne par assignation. C’est une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide car elle peut fonctionner avec la représentation interne de la classe conteneur.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de la version de modèle de `swap`, consultez l’exemple de code pour la classe membre [multiset::swap](../standard-library/multiset-class.md#swap).
