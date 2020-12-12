---
description: 'En savoir plus sur : &lt; chaîne&gt;'
title: '&lt;string&gt;'
ms.date: 11/04/2016
f1_keywords:
- string/std::<string>
- <string>
helpviewer_keywords:
- string header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: 4a5598189be96cb15ff423f57e45fd91e2d93216
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183540"
---
# <a name="ltstringgt"></a>&lt;string&gt;

Définit le modèle de classe `basic_string` de conteneur et divers modèles de prise en charge.

Pour plus d’informations sur `basic_string`, consultez [basic_string, classe](../standard-library/basic-string-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
#include <string>
```

## <a name="remarks"></a>Notes

Le langage C++ et la bibliothèque standard C++ prennent en charge deux types de chaînes :

- tableaux de caractères se terminant par un caractère Null et souvent appelés chaînes C ;

- objets de modèle de classe, de type `basic_string` , qui gèrent tous les **`char`** arguments de modèle de type.

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[string](../standard-library/string-typedefs.md#string)|Type qui décrit une spécialisation du modèle de classe `basic_string` avec des éléments de type **`char`** en tant que `string` .|
|[wstring](../standard-library/string-typedefs.md#wstring)|Type qui décrit une spécialisation du modèle de classe `basic_string` avec des éléments de type **`wchar_t`** en tant que `wstring` .|
|[u16string](../standard-library/string-typedefs.md#u16string)|Type qui décrit une spécialisation du modèle de classe `basic_string` en fonction d’éléments de type **`char16_t`** .|
|[u32string](../standard-library/string-typedefs.md#u32string)|Type qui décrit une spécialisation du modèle de classe `basic_string` en fonction d’éléments de type **`char32_t`** .|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur +](../standard-library/string-operators.md#op_add)|Concatène deux objets string.|
|[opérateur ! =](../standard-library/string-operators.md#op_neq)|Teste si l'objet string situé à gauche de l'opérateur n'est pas égal à l'objet string situé à droite.|
|[opérateur = =](../standard-library/string-operators.md#op_eq_eq)|Teste si l'objet string situé à gauche de l'opérateur est égal à l'objet string situé à droite.|
|[<d’opérateur ](../standard-library/string-operators.md#op_lt)|Teste si l'objet string situé à gauche de l'opérateur est inférieur à l'objet string situé à droite.|
|[<opérateur =](../standard-library/string-operators.md#op_lt_eq)|Teste si l'objet string situé à gauche de l'opérateur est inférieur ou égal à l'objet string situé à droite.|
|[<d’opérateur \<](../standard-library/string-operators.md#op_lt_lt)|Fonction de modèle qui insère une chaîne dans le flux de sortie.|
|[>d’opérateur ](../standard-library/string-operators.md#op_gt)|Teste si l'objet string situé à gauche de l'opérateur est supérieur à l'objet string situé à droite.|
|[>opérateur =](../standard-library/string-operators.md#op_gt_eq)|Teste si l'objet string situé à gauche de l'opérateur est supérieur ou égal à l'objet string situé à droite.|
|[>>d’opérateur ](../standard-library/string-operators.md#op_gt_gt)|Fonction de modèle qui extrait une chaîne du flux d'entrée.|

### <a name="specialized-template-functions"></a>Fonctions avec modèle spécialisé

|Nom|Description|
|-|-|
|`hash`|Produit un hachage d’une chaîne.|
|[swap](../standard-library/string-functions.md#swap)|Échange les tableaux de caractères de deux chaînes.|
|[stod](../standard-library/string-functions.md#stod)|Convertit une séquence de caractères en **`double`** .|
|[stof](../standard-library/string-functions.md#stof)|Convertit une séquence de caractères en **`float`** .|
|[stoi](../standard-library/string-functions.md#stoi)|Convertit une séquence de caractères en entier.|
|[stold](../standard-library/string-functions.md#stold)|Convertit une séquence de caractères en **`long double`** .|
|[stoll](../standard-library/string-functions.md#stoll)|Convertit une séquence de caractères en **`long long`** .|
|[stoul](../standard-library/string-functions.md#stoul)|Convertit une séquence de caractères en **`unsigned long`** .|
|[stoull](../standard-library/string-functions.md#stoull)|Convertit une séquence de caractères en **`unsigned long long`** .|
|[to_string](../standard-library/string-functions.md#to_string)|Convertit une valeur en `string`.|
|[to_wstring](../standard-library/string-functions.md#to_wstring)|Convertit une valeur en `string` large.|

### <a name="functions"></a>Fonctions

|Fonction|Description|
|-|-|
|[Modèle getline](../standard-library/string-functions.md#getline)|Extrait des chaînes du flux d'entrée, ligne par ligne.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[Classe basic_string](../standard-library/basic-string-class.md)|Modèle de classe qui décrit les objets pouvant stocker une séquence d’objets de type caractère arbitraires.|
|[Struct char_traits](../standard-library/char-traits-struct.md)|Modèle de classe qui décrit les attributs associés à un caractère de type CharType|

### <a name="specializations"></a>Spécialisations

|Nom|Description|
|-|-|
|[\<char>Struct char_traits](../standard-library/char-traits-char-struct.md)|Struct qui est une spécialisation de la structure de modèle `char_traits` \<CharType> en un élément de type **`char`** .|
|[char_traits<wchar_t struct>](../standard-library/char-traits-wchar-t-struct.md)|Struct qui est une spécialisation de la structure de modèle `char_traits` \<CharType> en un élément de type **`wchar_t`** .|
|[char_traits<char16_t struct>](../standard-library/char-traits-char16-t-struct.md)|Struct qui est une spécialisation de la structure de modèle `char_traits` \<CharType> en un élément de type **`char16_t`** .|
|[char_traits<char32_t struct>](../standard-library/char-traits-char32-t-struct.md)|Struct qui est une spécialisation de la structure de modèle `char_traits` \<CharType> en un élément de type **`char32_t`** .|

## <a name="requirements"></a>Spécifications

- **En-tête :**\<string>

- **Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
