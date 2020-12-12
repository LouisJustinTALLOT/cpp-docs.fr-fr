---
description: 'En savoir plus sur : hash &lt; string_view &gt; spécialisation'
title: spécialisation de la string_view de hachage &lt; &gt;
ms.date: 04/19/2019
f1_keywords:
- xstring/basic_string_view::hash
helpviewer_keywords:
- std::basic_string_view::hash
ms.openlocfilehash: cf4012752bbd8b3531920e78d612e78479de4b3d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183683"
---
# <a name="hashltstring_viewgt-specialization"></a>spécialisation de la string_view de hachage &lt; &gt;

Spécialisation de modèle qui produit une valeur de hachage en fonction d’un string_view.

```cpp
template <class CharType, class Traits>
struct hash<basic_string_view<CharType, Traits>>
{
    typedef basic_string_view<CharType, Traits> argument_type;
    typedef size_t result_type;

    size_t operator()(const basic_string_view<CharType, Traits>) const
        noexcept;
};
```

### <a name="remarks"></a>Notes

Le hachage d’un string_view est égal au hachage de l’objet String sous-jacent.

### <a name="example"></a>Exemple

```cpp
//compile with: /std:c++17
#include <string>
#include <string_view>
#include <iostream>

using namespace std;

int main()
{
    string_view sv{ "Hello world" };
    string s{ "Hello world" };
    cout << boolalpha << (hash<string_view>{}(sv)
        == hash<string>{}(s)); // true
}
```
