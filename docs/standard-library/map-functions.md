---
title: '&lt;map&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
ms.openlocfilehash: e7876b37bfc006eaecf2f1e36273c5ae8689dad4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243291"
---
# <a name="ltmapgt-functions"></a>&lt;map&gt;, fonctions

## <a name="swap_multimap"></a> swap (map)

Échange les éléments de deux classes map.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    map<Key, Traits, Compare, Alloctor>& left,
    map<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
La carte qui fournit les éléments à échanger ou mappage dont les éléments doivent être échangés avec ceux du mappage *gauche*.

*Gauche*\
Le mappage dont les éléments doivent être échangés avec ceux du mappage *droit*.

### <a name="remarks"></a>Notes

La fonction de modèle est un algorithme spécialisé sur la classe de conteneur map pour exécuter la fonction membre `left`.[ échange](../standard-library/map-class.md#swap)( `right`). Il s’agit d’une instance du classement partiel des modèles de fonction par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle, **template** \< **class T**> **void swap**( **T&** , **T&** ), dans la classe d’algorithme fonctionne par assignation et est une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide, car elle peut fonctionner avec la représentation interne de la classe de conteneur.

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise la version de modèle de `swap`, consultez l’exemple de code de la fonction membre [map::swap](../standard-library/map-class.md#swap).

## <a name="swap"></a> swap (multimap)

Échange les éléments de deux multimaps.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,
    multimap<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
La classe multimap qui fournit les éléments à échanger ou multimap dont les éléments doivent être échangés avec ceux du multimap *gauche*.

*Gauche*\
Multimap dont les éléments doivent être échangés avec ceux du multimap *droit*.

### <a name="remarks"></a>Notes

La fonction de modèle est un algorithme spécialisé sur la carte de classe de conteneur à exécuter sur la classe conteneur multimap pour exécuter la fonction membre `left`.[ échange](../standard-library/multimap-class.md#swap) (`right`). Il s’agit d’une instance du classement partiel des modèles de fonction par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle, **template** \< **class T**> **void swap**( **T&** , **T&** ), dans la classe d’algorithme fonctionne par assignation et est une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide, car elle peut fonctionner avec la représentation interne de la classe de conteneur.

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise la version de modèle de `swap`, consultez l’exemple de code de la fonction membre [multimap::swap](../standard-library/multimap-class.md#swap).
