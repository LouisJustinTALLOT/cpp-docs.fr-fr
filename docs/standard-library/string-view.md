---
title: '&lt;string_view&gt;'
ms.date: 04/18/2019
helpviewer_keywords:
- string_view header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 8952416cf37fc4d8d281d6ced9b8264495ec3799
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346977"
---
# <a name="ltstringviewgt"></a>&lt;string_view&gt;

Définit le modèle de classe `basic_string_view` et des types et opérateurs. (Nécessite l’option du compilateur [std : c ++ 17](../build/reference/std-specify-language-standard-version.md) ou version ultérieure.)

## <a name="syntax"></a>Syntaxe

```cpp
#include <string_view>
```

## <a name="remarks"></a>Notes

La famille de string_view des spécialisations de modèle fournit un moyen efficace de passer un handle en lecture seule protégé contre les exceptions, et non propriétaire pour les données de caractères des objets de type chaîne avec le premier élément de la séquence à la position zéro. Un paramètre de fonction de type `string_view` (qui est un typedef pour `basic_string_view<char>`) peut accepter des arguments tels que `std::string`, **char\***, ou toute autre classe de type chaîne de caractères étroits pour lequel implicite conversion en `string_view` est défini. De même, un paramètre de `wstring_view`, `u16string_view` ou `u32string_view` peut accepter n’importe quel type de chaîne pour lequel une conversion implicite est définie. Pour plus d’informations, consultez [basic_string_view classe](../standard-library/basic-string-view-class.md).

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[string_view](../standard-library/string-view-typedefs.md#string_view)|Une spécialisation du modèle de classe `basic_string_view` avec des éléments de type **char**.|
|[wstring_view](../standard-library/string-view-typedefs.md#wstring_view)|Une spécialisation du modèle de classe `basic_string_view` avec des éléments de type **wchar_t**.|
|[u16string_view](../standard-library/string-view-typedefs.md#u16string_view)|Une spécialisation du modèle de classe `basic_string_view` avec des éléments de type `char16_t`.|
|[u32string_view](../standard-library/string-view-typedefs.md#u32string_view)|Une spécialisation du modèle de classe `basic_string_view` avec des éléments de type `char32_t`.|

### <a name="operators"></a>Opérateurs

Le \<string_view > opérateurs peuvent comparer `string_view` sur les objets de n’importe quel convertibles en types de chaînes.

|Opérateur|Description|
|-|-|
|[!=, opérateur](../standard-library/string-view-operators.md#op_neq)|Teste si l’objet situé à gauche de l’opérateur n’est pas égal à l’objet situé à droite.|
|[operator==](../standard-library/string-view-operators.md#op_eq_eq)|Teste si l’objet situé à gauche de l’opérateur est égal à l’objet situé à droite.|
|[operator<](../standard-library/string-view-operators.md#op_lt)|Teste si l’objet sur le côté gauche de l’opérateur est inférieur à l’objet situé à droite.|
|[operator<=](../standard-library/string-view-operators.md#op_lt_eq)|Teste si l’objet situé à gauche de l’opérateur est inférieur ou égal à l’objet situé à droite.|
|[operator<\<](../standard-library/string-view-operators.md#op_lt_lt)|Une fonction de modèle qui insère un `string_view` dans un flux de sortie.|
|[operator>](../standard-library/string-view-operators.md#op_gt)|Teste si l’objet sur le côté gauche de l’opérateur est supérieur à l’objet situé à droite.|
|[operator>=](../standard-library/string-view-operators.md#op_gt_eq)|Teste si l’objet situé à gauche de l’opérateur est supérieur ou égal à l’objet situé à droite.|

### <a name="literals"></a>Littéraux

|Opérateur|Description|
|-|-|
|[sv](../standard-library/string-view-operators.md#op_sv)|Construit un `string_view`, `wstring_view`, `u16string_view`, ou `u32string_view` selon le type de littéral de chaîne à laquelle il est ajouté.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[Classe basic_string_view](../standard-library/basic-string-view-class.md)|Un modèle de classe qui fournit une vue en lecture seule dans une séquence d’objets de type caractère arbitraires.|
|[hash](string-view-hash.md)|Objet de fonction qui génère une valeur de hachage pour un string_view.|

## <a name="requirements"></a>Configuration requise

- **En-tête :** \<string_view >

- **Espace de noms :** std

- **Option du compilateur :** std : c ++ 17 (ou version ultérieure)

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
