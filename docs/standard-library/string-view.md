---
title: '&lt;string_view&gt;'
ms.date: 04/18/2019
helpviewer_keywords:
- string_view header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 47924c3d6bd1a2f45cdbac648f4f563c57ce8939
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459117"
---
# <a name="ltstringviewgt"></a>&lt;string_view&gt;

Définit le modèle `basic_string_view` de classe et les types et opérateurs associés. (Nécessite l’option du compilateur [std: c++ 17](../build/reference/std-specify-language-standard-version.md) ou une version ultérieure.)

## <a name="syntax"></a>Syntaxe

```cpp
#include <string_view>
```

## <a name="remarks"></a>Notes

La famille string_view de spécialisations de modèle offre un moyen efficace de passer un handle en lecture seule, sans exception et non propriétaire aux données caractères de tout objet de type chaîne avec le premier élément de la séquence à la position zéro. Un paramètre de fonction de `string_view` type (qui est un typedef `basic_string_view<char>`pour) peut accepter des arguments `std::string`tels **que\*char**, ou toute autre classe de type chaîne de caractères étroits pour laquelle une conversion implicite en `string_view`est défini. De même, un paramètre de `wstring_view` `u16string_view` ou `u32string_view` peut accepter n’importe quel type de chaîne pour lequel une conversion implicite est définie. Pour plus d’informations, consultez [basic_string_view, classe](../standard-library/basic-string-view-class.md).

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[string_view](../standard-library/string-view-typedefs.md#string_view)|Spécialisation du modèle `basic_string_view` de classe avec des éléments de type **char**.|
|[wstring_view](../standard-library/string-view-typedefs.md#wstring_view)|Spécialisation du modèle `basic_string_view` de classe avec les éléments de type **wchar_t**.|
|[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)|Spécialisation du modèle `basic_string_view` de classe avec des éléments de `char16_t`type.|
|[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)|Spécialisation du modèle `basic_string_view` de classe avec des éléments de `char32_t`type.|

### <a name="operators"></a>Opérateurs

Les \<opérateurs de > string_view peuvent `string_view` comparer des objets à des objets de n’importe quel type de chaîne convertible.

|Opérateur|Description|
|-|-|
|[!=, opérateur](../standard-library/string-view-operators.md#op_neq)|Teste si l’objet situé à gauche de l’opérateur n’est pas égal à l’objet situé à droite.|
|[operator==](../standard-library/string-view-operators.md#op_eq_eq)|Teste si l’objet situé à gauche de l’opérateur est égal à l’objet situé à droite.|
|[operator<](../standard-library/string-view-operators.md#op_lt)|Teste si l’objet situé à gauche de l’opérateur est inférieur à l’objet situé à droite.|
|[operator<=](../standard-library/string-view-operators.md#op_lt_eq)|Teste si l’objet situé à gauche de l’opérateur est inférieur ou égal à l’objet situé à droite.|
|[operator<\<](../standard-library/string-view-operators.md#op_lt_lt)|Fonction de modèle qui insère un dans `string_view` un flux de sortie.|
|[operator>](../standard-library/string-view-operators.md#op_gt)|Teste si l’objet situé à gauche de l’opérateur est supérieur à l’objet situé à droite.|
|[operator>=](../standard-library/string-view-operators.md#op_gt_eq)|Teste si l’objet situé à gauche de l’opérateur est supérieur ou égal à l’objet situé à droite.|

### <a name="literals"></a>Littéraux

|Opérateur|Description|
|-|-|
|[sv](../standard-library/string-view-operators.md#op_sv)|`string_view`Construit un `wstring_view` ,,ou`u32string_view` en fonction du type du littéral de chaîne auquel il est ajouté. `u16string_view`|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[Classe basic_string_view](../standard-library/basic-string-view-class.md)|Modèle de classe qui fournit une vue en lecture seule dans une séquence d’objets de type caractère arbitraires.|
|[hash](string-view-hash.md)|Objet de fonction qui produit une valeur de hachage pour un string_view.|

## <a name="requirements"></a>Configuration requise

- **En-tête:** \<string_view >

- **Espace de noms :** std

- **Option du compilateur:** std: c++ 17 (ou version ultérieure)

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
