---
title: '&lt;Type Variant&gt;'
ms.date: 04/04/2019
f1_keywords:
- <variant>
helpviewer_keywords:
- <variant>
ms.openlocfilehash: 7a812ccc3c8cb2a660c01ad2b17ea75b5d5c9542
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268441"
---
# <a name="ltvariantgt"></a>&lt;Type Variant&gt;

Un objet variant contienne et gère une valeur. Si la variante conserve une valeur, type de cette valeur doit être un des types d’arguments de modèle données vers un variant. Ces arguments template sont appelés des alternatives.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<variante >

**Espace de noms :** std

## <a name="members"></a>Membres

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[operator==](../standard-library/forward-list-operators.md#op_eq_eq)|Teste si l’objet variant sur le côté gauche de l’opérateur est égal à l’objet variant sur le côté droit.|
|[!=, opérateur](../standard-library/forward-list-operators.md#op_neq)|Teste si l’objet variant sur le côté gauche de l’opérateur n’est pas égal à l’objet variant sur le côté droit.|
|[operator<](../standard-library/forward-list-operators.md#op_lt)|Teste si l’objet variant sur le côté gauche de l’opérateur est inférieur à l’objet variant sur le côté droit.|
|[operator<=](../standard-library/forward-list-operators.md#op_lt_eq)|Teste si la variante de l’objet sur le côté gauche de l’opérateur est inférieur ou égal à l’objet variant sur le côté droit.|
|[operator>](../standard-library/forward-list-operators.md#op_gt)|Teste si l’objet variant sur le côté gauche de l’opérateur est supérieur à l’objet variant sur le côté droit.|
|[operator>=](../standard-library/forward-list-operators.md#op_lt_eq)|Teste si l’objet variant sur le côté gauche de l’opérateur est supérieur ou égal à l’objet variant sur le côté droit.|

### <a name="functions"></a>Fonctions

|||
|-|-|
|[get](../standard-library/variant-functions.md#get)|Obtient la variante d’un objet.|
|[get_if](../standard-library/variant-functions.md#get_if)|Obtient la variante d’un objet s’il existe.|
|[holds_alternative](../standard-library/variant-functions.md#holds_alternative)|Retourner **true** si une variante existe.|
|[swap](../standard-library/variant-functions.md#swap)|Échange un **variante**.|
|[visite](../standard-library/variant-functions.md#visit)|Déplace vers la prochaine **variante**.|

### <a name="classes"></a>Classes

|||
|-|-|
|[bad_variant_access](../standard-library/bad-variant-access-class.md)|Objets levés à accès non valide de rapport à la valeur d’un objet variant.|
|[Type Variant](../standard-library/variant.md)|Un objet soit contenir une valeur d’un de ses autres types, ou aucune valeur.|

### <a name="structs"></a>Structs

|||
|-|-|
|[hash](../standard-library/hash-structure.md)||
|[le modèle Monostate](../standard-library/monostate-structure.md)|Un autre type pour une variante pour rendre la valeur par défaut de type variant constructible.|
|[uses_allocator](../standard-library/uses-allocator-structure.md)||
|[variant_alternative](../standard-library/variant-alternative-structure.md)|Assiste les objets de type variant.|
|[variant_size](../standard-library/variant-size-structure.md)|Assiste les objets de type variant.|

### <a name="objects"></a>Objets

|||
|-|-|
|[variant_npos](../standard-library/variant-functions.md#variant_npos)||

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
