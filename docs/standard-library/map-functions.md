---
title: '&lt;map&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
ms.openlocfilehash: 8cc4a82e08963902f9ba5c21ace759c47bdd0014
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228217"
---
# <a name="ltmapgt-functions"></a>&lt;map&gt;, fonctions

## <a name="swap-map"></a><a name="swap_multimap"></a>swap (Map)

Échange les éléments de deux classes map.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    map<Key, Traits, Compare, Alloctor>& left,
    map<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Carte qui fournit les éléments à permuter, ou mappage dont les éléments doivent être échangés avec ceux de la carte de *gauche*.

*gauche*\
Mappage dont les éléments doivent être échangés avec ceux du mappage de *droite*.

### <a name="remarks"></a>Notes

La fonction de modèle est un algorithme spécialisé sur la classe de conteneur MAP pour exécuter la fonction membre `left` .[ échange](../standard-library/map-class.md#swap)( `right` ). Il s’agit d’une instance de l’ordonnancement partiel des modèles de fonctions par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle, **`template`** \< **class T**> **void swap**( **t&**, **t&**), dans la classe d’algorithme fonctionne par assignation et est une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide car elle peut fonctionner avec la représentation interne de la classe conteneur.

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise la version de modèle de `swap`, consultez l’exemple de code de la fonction membre [map::swap](../standard-library/map-class.md#swap).

## <a name="swap-multimap"></a><a name="swap"></a>échange (Multimap)

Échange les éléments de deux multimaps.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,
    multimap<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Multimap qui fournit les éléments à échanger ou Multimap dont les éléments doivent être échangés avec ceux du Multimap à *gauche*.

*gauche*\
Multimap dont les éléments doivent être échangés avec ceux du *droit*Multimap.

### <a name="remarks"></a>Notes

La fonction de modèle est un algorithme spécialisé sur la classe de conteneur MAP pour s’exécuter sur la classe de conteneur Multimap pour exécuter la fonction membre `left` .[ échange](../standard-library/multimap-class.md#swap) ( `right` ). Il s’agit d’une instance de l’ordonnancement partiel des modèles de fonctions par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle, **`template`** \< **class T**> **void swap**( **t&**, **t&**), dans la classe d’algorithme fonctionne par assignation et est une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide car elle peut fonctionner avec la représentation interne de la classe conteneur.

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise la version de modèle de `swap`, consultez l’exemple de code de la fonction membre [multimap::swap](../standard-library/multimap-class.md#swap).
