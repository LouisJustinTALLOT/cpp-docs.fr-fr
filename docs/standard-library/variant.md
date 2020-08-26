---
title: '&lt;variant&gt;'
ms.date: 04/04/2019
f1_keywords:
- <variant>
helpviewer_keywords:
- <variant>
ms.openlocfilehash: 1a3c861c96fedb7ef95eec66f95888ddc092bed4
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835660"
---
# <a name="ltvariantgt"></a>&lt;variant&gt;

Un objet variant contient et gère une valeur. Si le variant contient une valeur, le type de cette valeur doit être l’un des types d’arguments template donnés à la variante. Ces arguments template sont appelés alternatives.

## <a name="requirements"></a>Configuration requise

**En-tête :**\<variant>

**Espace de noms :** std

## <a name="members"></a>Membres

### <a name="operators"></a>Opérateurs

|Nom|Description|
|-|-|
|[opérateur = =](../standard-library/forward-list-operators.md#op_eq_eq)|Teste si l’objet variant situé à gauche de l’opérateur est égal à l’objet variant situé à droite.|
|[opérateur ! =](../standard-library/forward-list-operators.md#op_neq)|Teste si l’objet variant situé à gauche de l’opérateur n’est pas égal à l’objet variant situé à droite.|
|[<d’opérateur ](../standard-library/forward-list-operators.md#op_lt)|Teste si l’objet variant situé à gauche de l’opérateur est inférieur à l’objet variant situé à droite.|
|[<opérateur =](../standard-library/forward-list-operators.md#op_lt_eq)|Teste si l’objet variant situé à gauche de l’opérateur est inférieur ou égal à l’objet variant situé à droite.|
|[>d’opérateur ](../standard-library/forward-list-operators.md#op_gt)|Teste si l’objet variant situé à gauche de l’opérateur est supérieur à l’objet variant situé à droite.|
|[>opérateur =](../standard-library/forward-list-operators.md#op_lt_eq)|Teste si l’objet variant situé à gauche de l’opérateur est supérieur ou égal à l’objet variant situé à droite.|

### <a name="functions"></a>Functions

|Nom|Description|
|-|-|
|[get](../standard-library/variant-functions.md#get)|Obtient le variant d’un objet.|
|[get_if](../standard-library/variant-functions.md#get_if)|Obtient la variante d’un objet, le cas échéant.|
|[holds_alternative](../standard-library/variant-functions.md#holds_alternative)|Retourne **`true`** si un variant existe.|
|[swap](../standard-library/variant-functions.md#swap)|Permute une **variante**.|
|[consultez](../standard-library/variant-functions.md#visit)|Passe à la **variante**suivante.|

### <a name="classes"></a>Classes

|Nom|Description|
|-|-|
|[bad_variant_access](../standard-library/bad-variant-access-class.md)|Objets levés pour signaler des accès non valides à la valeur d’un objet variant.|
|[variant](../standard-library/variant.md)|Objet qui doit contenir une valeur de l’un de ses autres types, ou aucune valeur.|

### <a name="structs"></a>Structures

|Nom|Description|
|-|-|
|[hash](../standard-library/hash-structure.md)||
|[monoétat](../standard-library/monostate-structure.md)|Autre type pour un variant pour rendre le type Variant constructible par défaut.|
|[uses_allocator](../standard-library/uses-allocator-structure.md)||
|[variant_alternative](../standard-library/variant-alternative-structure.md)|Aide les objets variants.|
|[variant_size](../standard-library/variant-size-structure.md)|Aide les objets variants.|

### <a name="objects"></a>Objets

|Nom|Description|
|-|-|
|[variant_npos](../standard-library/variant-functions.md#variant_npos)||

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
