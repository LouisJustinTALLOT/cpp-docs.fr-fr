---
description: 'En savoir plus sur : &lt; type_traits&gt;'
title: '&lt;type_traits&gt;'
ms.date: 02/21/2019
f1_keywords:
- <type_traits>
helpviewer_keywords:
- typetrait header
- type_traits
ms.assetid: 2260b51f-8160-4c66-a82f-00b534cb60d4
ms.openlocfilehash: cf7bb4a5bf73eb49526926c151ffbbd0b55fda5b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226491"
---
# <a name="lttype_traitsgt"></a>&lt;type_traits&gt;

Définit des modèles pour les constantes au moment de la compilation qui fournissent des informations sur les propriétés de leurs arguments de type, ou produisent des types transformés.

## <a name="syntax"></a>Syntaxe

```cpp
#include <type_traits>
```

## <a name="remarks"></a>Notes

Les classes et les modèles dans \<type_traits> sont utilisés pour prendre en charge l’inférence de type, la classification et la transformation au moment de la compilation. Ils sont également utilisés pour détecter les erreurs liées au type et pour vous aider à optimiser votre code générique. Les caractéristiques de type unaire décrivent une propriété d’un type, les caractéristiques de type binaire décrivent une relation entre les types et les caractéristiques de transformation modifient une propriété d’un type.

La classe d’assistance `integral_constant` et ses spécialisations de modèle `true_type` et `false_type` constituent les classes de base pour les prédicats de type. Un *prédicat de type* est un modèle qui accepte un ou plusieurs arguments de type. Lorsqu’un prédicat de type a la *valeur true*, il est publiquement dérivé, directement ou indirectement, de [true_type](../standard-library/type-traits-typedefs.md#true_type). Lorsqu’un prédicat de type a la *valeur false*, il est publiquement dérivé, directement ou indirectement, de [false_type](../standard-library/type-traits-typedefs.md#false_type).

Un *modificateur de type* ou une *caractéristique de transformation* est un modèle qui accepte un ou plusieurs arguments de modèle et possède un seul membre `type`, qui est un synonyme du type modifié.

### <a name="alias-templates"></a>Modèles d'alias

Pour simplifier les expressions de traits de type, les [modèles d’alias](../cpp/aliases-and-typedefs-cpp.md) pour `typename some_trait<T>::type` sont fournis, où *some_trait* est le nom du modèle de classe. Par exemple, [add_const](../standard-library/add-const-class.md) a un modèle d’alias pour son type, `add_const_t`, défini comme suit :

```cpp
template <class T>
using add_const_t = typename add_const<T>::type;
```

Il s’agit des alias fournis pour les `type` membres :

:::row:::
   :::column:::
      `add_const_t`\
      `add_cv_t`\
      `add_lvalue_reference_t`\
      `add_pointer_t`\
      `add_rvalue_reference_t`\
      `add_volatile_t`\
      `aligned_storage_t`\
      `aligned_union_t`\
   :::column-end:::
   :::column:::
      `common_type_t`\
      `conditional_t`\
      `decay_t`\
      `enable_if_t`\
      `invoke_result_t`\
      `make_signed_t`\
      `make_unsigned_t`\
      `remove_all_extents_t`\
   :::column-end:::
   :::column:::
      `remove_const_t`\
      `remove_cv_t`\
      `remove_extent_t`\
      `remove_pointer_t`\
      `remove_reference_t`\
      `remove_volatile_t`\
      `result_of_t`\
      `underlying_type_t`\
   :::column-end:::
:::row-end:::

### <a name="classes"></a>Classes

Typedefs et classe d’assistance

|Nom|Description|
|-|-|
|[integral_constant](../standard-library/integral-constant-class-bool-constant-class.md)|Crée une constante intégrale à partir d’un type et d’une valeur.|
|[true_type](../standard-library/type-traits-typedefs.md#true_type)|Contient une constante intégrale avec la valeur true.|
|[false_type](../standard-library/type-traits-typedefs.md#false_type)|Contient une constante intégrale avec la valeur false.|

Catégories de type principal

|Nom|Description|
|-|-|
|[is_void](../standard-library/is-void-class.md)|Teste si le type est **`void`** .|
|[is_null_pointer](../standard-library/is-null-pointer-class.md)|Teste si le type est `std::nullptr_t`.|
|[is_integral](../standard-library/is-integral-class.md)|Teste si le type est intégral.|
|[is_floating_point](../standard-library/is-floating-point-class.md)|Teste si le type est à virgule flottante.|
|[is_array](../standard-library/is-array-class.md)|Teste si le type est un tableau.|
|[is_pointer](../standard-library/is-pointer-class.md)|Teste si le type est un pointeur.|
|[is_lvalue_reference](../standard-library/is-lvalue-reference-class.md)|Teste si le type est une référence lvalue.|
|[is_rvalue_reference](../standard-library/is-rvalue-reference-class.md)|Teste si le type est une référence rvalue.|
|[is_member_object_pointer](../standard-library/is-member-object-pointer-class.md)|Teste si le type est un pointeur vers un objet membre.|
|[is_member_function_pointer](../standard-library/is-member-function-pointer-class.md)|Teste si le type est un pointeur vers une fonction membre.|
|[is_enum](../standard-library/is-enum-class.md)|Teste si le type est une énumération.|
|[is_union](../standard-library/is-union-class.md)|Teste si le type est une union.|
|[is_class](../standard-library/is-class-class.md)|Teste si le type est une classe.|
|[is_function](../standard-library/is-function-class.md)|Teste si le type est un type de fonction.|

Catégories de type composite

|Nom|Description|
|-|-|
|[is_reference](../standard-library/is-reference-class.md)|Teste si le type est une référence.|
|[is_arithmetic](../standard-library/is-arithmetic-class.md)|Teste si le type est arithmétique.|
|[is_fundamental](../standard-library/is-fundamental-class.md)|Teste si le type est **`void`** ou arithmétique.|
|[is_object](../standard-library/is-object-class.md)|Teste si le type est un type d'objet.|
|[is_scalar](../standard-library/is-scalar-class.md)|Teste si le type est scalaire.|
|[is_compound](../standard-library/is-compound-class.md)|Teste si le type n'est pas scalaire.|
|[is_member_pointer](../standard-library/is-member-pointer-class.md)|Teste si le type est un pointeur vers un membre.|

Propriétés type

|Nom|Description|
|-|-|
|[is_const](../standard-library/is-const-class.md)|Teste si le type est **`const`** .|
|[is_volatile](../standard-library/is-volatile-class.md)|Teste si le type est **`volatile`** .|
|[is_trivial](../standard-library/is-trivial-class.md)|Teste si le type est trivial.|
|[is_trivially_copyable](../standard-library/is-trivially-copyable-class.md)|Teste si le type peut être copié de façon triviale.|
|[is_standard_layout](../standard-library/is-standard-layout-class.md)|Teste si le type est un type de disposition standard.|
|[is_pod](../standard-library/is-pod-class.md)|Teste si le type est POD.|
|[is_literal_type](../standard-library/is-literal-type-class.md)|Teste si le type peut être une **`constexpr`** variable ou être utilisé dans une **`constexpr`** fonction.|
|[is_empty](../standard-library/is-empty-class.md)|Teste si le type est une classe vide.|
|[is_polymorphic](../standard-library/is-polymorphic-class.md)|Teste si le type est une classe polymorphe.|
|[is_abstract](../standard-library/is-abstract-class.md)|Teste si le type est une classe abstraite.|
|[is_final](../standard-library/is-final-class.md)|Teste si le type est un type de classe marqué `final`.|
|[is_aggregate](../standard-library/is-aggregate-class.md)||
|[is_signed](../standard-library/is-signed-class.md)|Teste si le type est un entier signé.|
|[is_unsigned](../standard-library/is-unsigned-class.md)|Teste si le type est un entier non signé.|
|[is_constructible](../standard-library/is-constructible-class.md)|Teste si le type est constructible à l’aide des types d’argument spécifiés.|
|[is_default_constructible](../standard-library/type-traits-functions.md#is_default_constructible)|Teste si le type a un constructeur par défaut.|
|[is_copy_constructible](../standard-library/type-traits-functions.md#is_copy_constructible)|Teste si le type a un constructeur de copie.|
|[is_move_constructible](../standard-library/type-traits-functions.md#is_move_constructible)|Teste si le type a un constructeur de déplacement.|
|[is_assignable](../standard-library/type-traits-functions.md#is_assignable)|Teste si le premier type peut se voir assigner une valeur du second type.|
|[is_copy_assignable](../standard-library/type-traits-functions.md#is_copy_assignable)|Teste si un type peut se voir assigner une valeur de référence const du type.|
|[is_move_assignable](../standard-library/type-traits-functions.md#is_move_assignable)|Teste si un type peut se voir assigner une référence rvalue du type.|
|[is_swappable](../standard-library/type-traits-functions.md#is_swappable)||
|[is_swappable_with](../standard-library/type-traits-functions.md#is_swappable_with)||
|[is_destructible](../standard-library/is-destructible-class.md)|Teste si le type est destructible.|
|[is_trivially_constructible](../standard-library/is-trivially-constructible-class.md)|Teste si le type n’utilise aucune opération non triviale lorsqu’il est construit à l’aide des types spécifiés.|
|[is_trivially_default_constructible](../standard-library/is-trivially-default-constructible-class.md)|Teste si le type n’utilise aucune opération non triviale lorsqu’il est construit par défaut.|
|[is_trivially_copy_constructible](../standard-library/is-trivially-copy-constructible-class.md)|Teste si le type n’utilise aucune opération non triviale lorsqu’il est construit par copie.|
|[is_trivially_move_constructible](../standard-library/type-traits-functions.md#is_trivially_move_constructible)|Teste si le type n’utilise aucune opération non triviale lorsqu’il est construit par déplacement.|
|[is_trivially_assignable](../standard-library/is-trivially-assignable-class.md)|Teste si les types peuvent être assignés et si l’assignation n’utilise aucune opération non triviale.|
|[is_trivially_copy_assignable](../standard-library/type-traits-functions.md#is_trivially_copy_assignable)|Teste si le type peut être assigné par copie et si l’assignation n’utilise aucune opération non triviale.|
|[is_trivially_move_assignable](../standard-library/type-traits-functions.md#is_trivially_move_assignable)|Teste si le type peut être assigné par déplacement et si l’assignation n’utilise aucune opération non triviale.|
|[is_trivially_destructible](../standard-library/is-trivially-destructible-class.md)|Teste si le type est destructible et si le destructeur n’utilise aucune opération non triviale.|
|[is_nothrow_constructible](../standard-library/is-nothrow-constructible-class.md)|Teste si le type est constructible et est connu comme ne levant pas d’exception quand il est construit à l’aide des types spécifiés.|
|[is_nothrow_default_constructible](../standard-library/is-nothrow-default-constructible-class.md)|Teste si le type est constructible par défaut et connu comme ne levant pas d’exception lorsqu’il est construit par défaut.|
|[is_nothrow_copy_constructible](../standard-library/is-nothrow-copy-constructible-class.md)|Teste si le type est constructible par copie et si le constructeur de copie est connu comme ne levant pas d’exception.|
|[is_nothrow_move_constructible](../standard-library/is-nothrow-move-constructible-class.md)|Teste si le type est constructible par déplacement et si le constructeur de déplacement est connu comme ne levant pas d’exception.|
|[is_nothrow_assignable](../standard-library/is-nothrow-assignable-class.md)|Teste si le type peut être assigné à l’aide du type spécifié et si l’assignation est connue comme ne levant pas d’exception.|
|[is_nothrow_copy_assignable](../standard-library/is-nothrow-copy-assignable-class.md)|Teste si le type peut être assigné par copie et si l’assignation est connue comme ne levant pas d’exception.|
|[is_nothrow_move_assignable](../standard-library/type-traits-functions.md#is_nothrow_move_assignable)|Teste si le type peut être assigné par déplacement et si l’assignation est connue comme ne levant pas d’exception.|
|[is_nothrow_swappable](../standard-library/type-traits-functions.md#is_nothrow_swappable)||
|[is_nothrow_swappable_with](../standard-library/type-traits-functions.md#is_nothrow_swappable_with)||
|[is_nothrow_destructible](../standard-library/is-nothrow-destructible-class.md)|Teste si le type est destructible et si le destructeur est connu comme ne levant pas d’exception.|
|`has_virtual_destructor`|Teste si le type a un destructeur virtuel.|
|`has_unique_object_representations`||
| [is_invocable](is-invocable-classes.md) | Teste si un type pouvant être appelé peut être appelé à l’aide des types d’arguments spécifiés.<br/> Ajouté en C++ 17. |
| [is_invocable_r](is-invocable-classes.md) | Teste si un type pouvant être appelé peut être appelé à l’aide des types d’arguments spécifiés et que le résultat peut être converti dans le type spécifié.<br/> Ajouté en C++ 17. |
| [is_nothrow_invocable](is-invocable-classes.md) | Teste si un type pouvant être appelé peut être appelé à l’aide des types d’arguments spécifiés et s’il est connu de ne pas lever d’exceptions.<br/> Ajouté en C++ 17. |
| [is_nothrow_invocable_r](is-invocable-classes.md) | Teste si un type pouvant être appelé peut être appelé à l’aide des types d’arguments spécifiés et s’il est connu de ne pas lever d’exceptions, et le résultat peut être converti dans le type spécifié.<br/> Ajouté en C++ 17. |

Requêtes de propriétés de type

|Nom|Description|
|-|-|
|[alignment_of](../standard-library/alignment-of-class.md)|Obtient l’alignement d’un type.|
|[moteurs](../standard-library/rank-class.md)|Obtient le nombre de dimensions de tableau.|
|[étendue](../standard-library/extent-class.md)|Obtient le nombre d’éléments dans la dimension de tableau spécifiée.|

Relations de types

|Nom|Description|
|-|-|
|[is_same](../standard-library/is-same-class.md)|Teste si deux types sont identiques.|
|[is_base_of](../standard-library/is-base-of-class.md)|Teste si un type est une base d’un autre.|
|[is_convertible](../standard-library/is-convertible-class.md)|Teste si un type est convertible en un autre.|

Modifications const-volatile

|Nom|Description|
|-|-|
|[add_const](../standard-library/add-const-class.md)|Produit un **`const`** type à partir d’un type.|
|[add_volatile](../standard-library/add-volatile-class.md)|Produit un **`volatile`** type à partir d’un type.|
|[add_cv](../standard-library/add-cv-class.md)|Produit un **`const volatile`** type à partir d’un type.|
|[remove_const](../standard-library/remove-const-class.md)|Génère un type non const à partir d’un type.|
|[remove_volatile](../standard-library/remove-volatile-class.md)|Génère un type non volatile à partir d’un type.|
|[remove_cv](../standard-library/remove-cv-class.md)|Génère un type non const non volatile à partir d’un type.|

Modifications de référence

|Nom|Description|
|-|-|
|[add_lvalue_reference](../standard-library/add-lvalue-reference-class.md)|Génère une référence vers un type à partir d’un type.|
|[add_rvalue_reference](../standard-library/add-rvalue-reference-class.md)|Génère une référence rvalue vers un type à partir d’un type.|
|[remove_reference](../standard-library/remove-reference-class.md)|Génère un type non-référence à partir d’un type.|

Modifications de signe

|Nom|Description|
|-|-|
|[make_signed](../standard-library/make-signed-class.md)|Génère le type si signé, ou le plus petit type signé supérieur ou égal en taille au type.|
|[make_unsigned](../standard-library/make-unsigned-class.md)|Génère le type si non signé, ou le plus petit type non signé supérieur ou égal en taille au type.|

Modifications de tableau

|Nom|Description|
|-|-|
|[remove_all_extents](../standard-library/remove-all-extents-class.md)|Génère un type non-tableau à partir d’un type tableau.|
|[remove_extent](../standard-library/remove-extent-class.md)|Génère le type d’élément à partir d’un type tableau.|

Modifications de pointeur

|Nom|Description|
|-|-|
|[add_pointer](../standard-library/add-pointer-class.md)|Génère un pointeur vers un type à partir d’un type.|
|[remove_pointer](../standard-library/remove-pointer-class.md)|Génère un type à partir d’un pointeur vers un type.|

Autres transformations

|Nom|Description|
|-|-|
|[aligned_storage](../standard-library/aligned-storage-class.md)|Alloue la mémoire non initialisée pour un type aligné.|
|[aligned_union](../standard-library/aligned-union-class.md)|Alloue la mémoire non initialisée pour une union alignée avec un constructeur ou un destructeur non trivial.|
|[common_type](../standard-library/common-type-class.md)|Génère le type commun de tous les types du package de paramètres.|
|[conditionnel](../standard-library/conditional-class.md)|Si la condition est true, génère le premier type spécifié, sinon le second type spécifié.|
|[decay](../standard-library/decay-class.md)|Génère le type comme passé par la valeur. Crée un type non-référence, non const ou non volatile, ou crée un pointeur vers un type.|
|[enable_if](../standard-library/enable-if-class.md)|Si la condition est true, génère le type spécifié, sinon ne génère aucun type.|
|[invoke_result](invoke-result-class.md)|Détermine le type de retour du type pouvant être appelé qui accepte les types d’argument spécifiés. <br/>Ajouté en C++ 17. |
|[result_of](../standard-library/result-of-class.md)|Détermine le type de retour du type pouvant être appelé qui accepte les types d’argument spécifiés. <br/>Ajouté en C++ 14, déconseillé dans C++ 17. |
|[underlying_type](../standard-library/underlying-type-class.md)|Génère le type intégral sous-jacent pour un type d’énumération.|

Caractéristiques de l’opérateur logique

|Nom|Description|
|-|-|
|[conjonction](../standard-library/conjunction-class.md)||
|[disjonction](../standard-library/disjunction-class.md)||
|[négation](../standard-library/negation-class.md)||

## <a name="see-also"></a>Voir aussi

[\<functional>](../standard-library/functional.md)
