---
title: '&lt;hash_map&gt;, fonctions | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
ms.openlocfilehash: 4ae585c53fde68c580059532722ac5d0b019a3db
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845971"
---
# <a name="lthashmapgt-functions"></a>&lt;hash_map&gt;, fonctions

|||
|-|-|
|[swap](#swap)|[swap (hash_map)](#swap_hash_map)|

## <a name="swap_hash_map"></a>  swap (hash_map)

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_map, classe](../standard-library/unordered-map-class.md).

Échange les éléments de deux hash_maps.

```cpp
void swap(
    hash_map <Key, Type, Traits, Alloctor>& left,
    hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

`right` L’objet hash_map dont les éléments doivent être échangés avec ceux de la carte `left`.

`left` L’objet hash_map dont les éléments doivent être échangés avec ceux de la carte `right`.

### <a name="remarks"></a>Notes

La fonction de modèle est un algorithme spécialisé sur la classe de conteneur hash_map pour exécuter la fonction membre `left.`[swap](../standard-library/basic-ios-class.md#swap)*(right*). Il s’agit d’une instance de l’ordonnancement partiel des modèles de fonctions par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle, **template \<class T> void swap(T&, T&)**, dans le fichier d’en-tête d’algorithme fonctionne par assignation et est une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide, car elle peut fonctionner avec la représentation interne de la classe de conteneur.

## <a name="swap"></a>  swap

> [!NOTE]
> Cette API est obsolète. L’alternative est [unordered_multimap, classe](../standard-library/unordered-multimap-class.md).

Échange les éléments de deux hash_multimaps.

```cpp
void swap(
    hash_multimap <Key, Type, Traits, Alloctor>& left,
    hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

`right` La classe hash_multimap dont les éléments doivent être échangés avec ceux de la carte `left`.

`left` La classe hash_multimap dont les éléments doivent être échangés avec ceux de la carte `right`.

### <a name="remarks"></a>Notes

La fonction de modèle est un algorithme spécialisé sur la classe de conteneur hash_multimap pour exécuter la fonction membre `left.`[swap](../standard-library/hash-multimap-class.md#swap)*(right*`)`. Il s’agit d’une instance du classement partiel des modèles de fonction par le compilateur. Quand des fonctions de modèle sont surchargées de sorte que la correspondance du modèle avec l’appel de fonction n’est pas unique, le compilateur sélectionne la version la plus spécialisée de la fonction de modèle. La version générale de la fonction de modèle, **template \<class T> void swap(T&, T&)**, dans le fichier d’en-tête d’algorithme fonctionne par assignation et est une opération lente. La version spécialisée dans chaque conteneur est beaucoup plus rapide, car elle peut fonctionner avec la représentation interne de la classe de conteneur.

## <a name="see-also"></a>Voir aussi

[<hash_map>](../standard-library/hash-map.md)<br/>
