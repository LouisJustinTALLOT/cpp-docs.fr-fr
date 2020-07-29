---
title: '&lt;utility&gt;'
ms.date: 11/04/2016
f1_keywords:
- <utility>
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
ms.openlocfilehash: 1beade28ceec0f1552def4bc70c2e95e6b2aa24d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215437"
---
# <a name="ltutilitygt"></a>&lt;utility&gt;

Définit des types, des fonctions et des opérateurs de la bibliothèque standard C++ qui aident à construire et à gérer des paires d’objets qui sont utiles quand deux objets doivent être traités comme s’ils n’en étaient qu’un seul.

## <a name="requirements"></a>Spécifications

**En-tête :**\<utility>

**Espace de noms :** std

## <a name="remarks"></a>Notes

Les paires sont largement utilisées dans la bibliothèque standard C++. Elles sont nécessaires comme arguments et valeurs de retour pour diverses fonctions et comme types d’éléments pour des conteneurs tels que la [classe map](../standard-library/map-class.md) et la [classe multimap](../standard-library/multimap-class.md). L' \<utility> en-tête est automatiquement inclus par \<map> pour faciliter la gestion de leurs éléments de type paire clé/valeur.

> [!NOTE]
> L' \<utility> en-tête utilise l’instruction `#include <initializer_list>` . Elle fait également référence à `class tuple` comme défini dans \<tuple> .

## <a name="members"></a>Membres

### <a name="classes"></a>Classes

|Type|Description|
|-|-|
|[chars_format](../standard-library/chars-format-class.md)|Format à virgule flottante pour la conversion numérique primitive.|
|[tuple_element](../standard-library/tuple-element-class-tuple.md)|Classe qui encapsule le type d'un élément `pair`.|
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|Classe qui encapsule le nombre d'éléments `pair`.|

### <a name="objects"></a>Objets

|Modèle|Description|
|-|-|
|[index_sequence](../standard-library/utility-functions.md#index_sequence)|Modèle d’alias défini pour le cas courant où `T` est`std::size_t`  |
|[index_sequence_for](../standard-library/utility-functions.md#index_sequence_for)|Modèle d’alias d’assistance pour convertir un package de paramètres de type en une séquence d’index de la même longueur|
|[make_index_sequence](../standard-library/utility-functions.md#make_index_sequence)| Modèle d’alias d’assistance pour simplifier la création d’un `std::index_sequence` type. |
|[make_integer_sequence](../standard-library/utility-functions.md#make_integer_sequence)|Modèle d’alias d’assistance pour simplifier la création d’un `std::integer_sequence` type.|

### <a name="functions"></a>Fonctions

|Fonction|Description|
|-|-|
|[as_const](../standard-library/utility-functions.md#asconst)|Retourne le type.|
|[declval,](../standard-library/utility-functions.md#declval)|Évaluation de l’expression abrégée.|
|[échanger](../standard-library/utility-functions.md#exchange)|Assigne une nouvelle valeur à un objet et retourne son ancienne valeur.|
|[premier](../standard-library/utility-functions.md#forward)|Empêche que le type de référence (`lvalue` ou `rvalue`) de l'argument ne soit masqué par le transfert parfait.|
|[from_chars](../standard-library/utility-functions.md#from_chars)||
|[get](../standard-library/utility-functions.md#get)|Fonction qui obtient un élément d'un objet `pair`.|
|[make_pair](../standard-library/utility-functions.md#make_pair)|Fonction d'assistance de modèle qui sert à construire des objets de type `pair`, où les types de composants sont basés sur les types de données passés comme paramètres.|
|[move](../standard-library/utility-functions.md#move)|Retourne l'argument passé comme référence `rvalue`.|
|[move_if_noexcept](../standard-library/utility-functions.md#moveif)||
|[swap](../standard-library/utility-functions.md#swap)|Échange les éléments de deux objets `pair`.|
|[to_chars](../standard-library/utility-functions.md#to_chars)|Convertit la valeur en une chaîne de caractères.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur ! =](../standard-library/utility-operators.md#op_neq)|Teste si l'objet pair situé à gauche de l'opérateur n'est pas égal à l'objet pair situé à droite.|
|[opérateur = =](../standard-library/utility-operators.md#op_eq_eq)|Teste si l'objet pair situé à gauche de l'opérateur est égal à l'objet pair situé à droite.|
|[and\<](../standard-library/utility-operators.md#op_lt)|Teste si l'objet pair situé à gauche de l'opérateur est inférieur à l'objet pair situé à droite.|
|[and\<=](../standard-library/utility-operators.md#op_gt_eq)|Teste si l'objet pair situé à gauche de l'opérateur est inférieur ou égal à l'objet pair situé à droite.|
|[>d’opérateur](../standard-library/utility-operators.md#op_gt)|Teste si l'objet pair situé à gauche de l'opérateur est supérieur à l'objet pair situé à droite.|
|[>opérateur =](../standard-library/utility-operators.md#op_gt_eq)|Teste si l'objet pair situé à gauche de l'opérateur est supérieur ou égal à l'objet pair situé à droite.|

### <a name="structs"></a>Structs

|Struct|Description|
|-|-|
|[from_chars_result](../standard-library/from-chars-result-structure.md)|Struct utilisé pour `from_chars` .|
|[identity](../standard-library/identity-structure.md)|Struct qui fournit une définition de type comme paramètre de modèle.|
|[in_place_t](../standard-library/in-place-t-struct.md)|Comprend également des structs `in_place_type_t` et `in_place_index_t` .|
|[integer_sequence](../standard-library/integer-sequence-class.md)|Représente une séquence d'entiers.|
|[troubles](../standard-library/pair-structure.md)|Struct qui permet de traiter deux objets comme s'il s'agissait d'un objet unique.|
|[piecewise_construct_t](../standard-library/piecewise-construct-t-structure.md)|Type utilisé pour conserver une surcharge de constructeur et de fonction distincte.|
|[to_chars_result](../standard-library/to-chars-result-structure.md)|Struct utilisé pour `to_chars` .|

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
