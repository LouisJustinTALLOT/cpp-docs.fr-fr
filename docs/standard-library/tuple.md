---
title: '&lt;tuple&gt;'
ms.date: 11/04/2016
f1_keywords:
- <tuple>
helpviewer_keywords:
- tuple header
ms.assetid: e4ef5c2d-318b-44f6-8bce-fce4ecd796a3
ms.openlocfilehash: a391a77ea65a203a7eddde12046c5df89a77194a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447165"
---
# <a name="lttuplegt"></a>&lt;tuple&gt;

Définit un modèle `tuple` dont les instances détiennent des objets de types variables.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<tuple>

**Espace de noms :** std

## <a name="members"></a>Membres

### <a name="classes-and-structs"></a>Classes et structs

|||
|-|-|
|[tuple, classe](../standard-library/tuple-class.md)|Encapsule une séquence d’éléments de longueur fixe.|
|[tuple_element, classe](../standard-library/tuple-element-class-tuple.md)|Encapsule le type d'un élément `tuple`.|
|[tuple_size, classe](../standard-library/tuple-size-class-tuple.md)|Encapsule le nombre d'éléments `tuple`.|
|[uses_allocator](../standard-library/uses-allocator-structure.md)||

### <a name="objects"></a>Objets

|||
|-|-|
|[tuple_element_t](../standard-library/tuple-functions.md#tuple_element_t)||
|[tuple_size_v](../standard-library/tuple-functions.md#tuple_size_v)||

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[operator==](../standard-library/tuple-operators.md#op_eq_eq)|Comparaison d' `tuple` objets, EQUAL.|
|[!=, opérateur](../standard-library/tuple-operators.md#op_neq)|Comparaison d' `tuple` objets, non égal à.|
|[operator<](../standard-library/tuple-operators.md#op_lt)|Comparaison d' `tuple` objets, inférieur à.|
|[operator<=](../standard-library/tuple-operators.md#op_lt_eq)|Comparaison d' `tuple` objets, inférieur ou égal à.|
|[operator>](../standard-library/tuple-operators.md#op_gt)|Comparaison d' `tuple` objets, supérieur à.|
|[operator>=](../standard-library/tuple-operators.md#op_gt_eq)|Comparaison d' `tuple` objets, supérieur ou égal à.|

### <a name="functions"></a>Fonctions

|||
|-|-|
|[apply](../standard-library/tuple-functions.md#apply)|Appelle une fonction avec un tuple.|
|[forward_as_tuple](../standard-library/tuple-functions.md#forward)|Construit un tuple de références.|
|[get](../standard-library/tuple-functions.md#get)|Obtient un élément auprès d'un objet `tuple`.|
|[make_from_tuple](../standard-library/tuple-functions.md#make_from_tuple)|Raccourci pour créer un `tuple`.|
|[make_tuple](../standard-library/tuple-functions.md#make_tuple)|Crée un `tuple` à partir des valeurs de l’élément.|
|[swap](../standard-library/tuple-functions.md#swap)||
|[tie](../standard-library/tuple-functions.md#tie)|Crée un `tuple` à partir des références d’élément.|
|[tuple_cat](../standard-library/tuple-functions.md#tuple_cat)|Construit un objet Tuple avec une plage des éléments de type.|

## <a name="see-also"></a>Voir aussi

[\<array>](../standard-library/array.md)
