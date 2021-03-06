---
title: '&lt;string_view&gt;'
description: Vue d’ensemble `basic_string_view` , qui fait référence à une séquence contiguë constante d’objets de type char.
ms.date: 9/4/2020
helpviewer_keywords:
- string_view header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: f74f6c5855f71b0df46f585e874002cdb4308e42
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039909"
---
# <a name="ltstring_viewgt"></a>&lt;string_view&gt;

Définit le modèle de classe `basic_string_view` et les types et opérateurs associés. (Nécessite l’option du compilateur [std : c++ 17](../build/reference/std-specify-language-standard-version.md) ou une version ultérieure.)

## <a name="syntax"></a>Syntaxe

```cpp
#include <string_view>
```

## <a name="remarks"></a>Notes

La `string_view` famille de spécialisations de modèle offre un moyen efficace de passer un descripteur en lecture seule, sécurisé et non propriétaire aux données caractères de tout objet de type chaîne avec le premier élément de la séquence à la position zéro. Un paramètre de fonction de type `string_view` (qui est un typedef pour `basic_string_view<char>` ) peut accepter des arguments tels que `std::string` , `char*` ou toute autre classe de type chaîne de caractères étroits pour laquelle une conversion implicite vers `string_view` est définie. De même, un paramètre de `wstring_view` `u16string_view` ou `u32string_view` peut accepter n’importe quel type de chaîne pour lequel une conversion implicite est définie. Pour plus d’informations, consultez [Basic_string_view classe](../standard-library/basic-string-view-class.md).

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[string_view](../standard-library/string-view-typedefs.md#string_view)|Spécialisation du modèle de classe `basic_string_view` avec des éléments de type **`char`** .|
|[wstring_view](../standard-library/string-view-typedefs.md#wstring_view)|Spécialisation du modèle de classe `basic_string_view` avec des éléments de type **`wchar_t`** .|
|[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)|Spécialisation du modèle de classe `basic_string_view` avec des éléments de type **`char16_t`** .|
|[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)|Spécialisation du modèle de classe `basic_string_view` avec des éléments de type **`char32_t`** .|

### <a name="operators"></a>Opérateurs

Les \<string_view> opérateurs peuvent comparer des `string_view` objets à des objets de n’importe quel type de chaîne convertible.

|Opérateur|Description|
|-|-|
|[opérateur ! =](../standard-library/string-view-operators.md#op_neq)|Teste si l’objet situé à gauche de l’opérateur n’est pas égal à l’objet situé à droite.|
|[opérateur = =](../standard-library/string-view-operators.md#op_eq_eq)|Teste si l’objet situé à gauche de l’opérateur est égal à l’objet situé à droite.|
|[<d’opérateur ](../standard-library/string-view-operators.md#op_lt)|Teste si l’objet situé à gauche de l’opérateur est inférieur à l’objet situé à droite.|
|[<opérateur =](../standard-library/string-view-operators.md#op_lt_eq)|Teste si l’objet situé à gauche de l’opérateur est inférieur ou égal à l’objet situé à droite.|
|[<d’opérateur \<](../standard-library/string-view-operators.md#op_lt_lt)|Fonction de modèle qui insère un `string_view` dans un flux de sortie.|
|[>d’opérateur ](../standard-library/string-view-operators.md#op_gt)|Teste si l’objet situé à gauche de l’opérateur est supérieur à l’objet situé à droite.|
|[>opérateur =](../standard-library/string-view-operators.md#op_gt_eq)|Teste si l’objet situé à gauche de l’opérateur est supérieur ou égal à l’objet situé à droite.|

### <a name="literals"></a>Littéraux

|Opérateur|Description|
|-|-|
|[Ed](../standard-library/string-view-operators.md#op_sv)|Construit un `string_view` ,, `wstring_view` `u16string_view` ou `u32string_view` en fonction du type du littéral de chaîne auquel il est ajouté.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[Classe basic_string_view](../standard-library/basic-string-view-class.md)|Modèle de classe qui fournit une vue en lecture seule dans une séquence d’objets de type caractère arbitraires.|
|[hash](string-view-hash.md)|Objet de fonction qui produit une valeur de hachage pour un string_view.|

## <a name="requirements"></a>Configuration requise

- **En-tête :**\<string_view>

- **Espace de noms :** std

- **Option du compilateur :** [std : c++ 17](../build/reference/std-specify-language-standard-version.md) ou version ultérieure.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
