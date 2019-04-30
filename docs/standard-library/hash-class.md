---
title: hash, classe
ms.date: 11/04/2016
f1_keywords:
- functional/std::hash
- bitset/std::hash
- memory/std::hash
- string/std::hash
- system_error/std::hash
- thread/std::hash
- typeindex/std::hash
- vector/std::hash
- XSTDDEF/std::hash
- xstring/std::hash
helpviewer_keywords:
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
- std::hash [C++]
ms.assetid: e1b500c6-a5c8-4f6f-ad33-7ec52eb8e2e4
ms.openlocfilehash: 2f7206e3764df384004b78e6df2127833a784f70
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405090"
---
# <a name="hash-class"></a>hash, classe

Calcule le code de hachage pour une valeur.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
struct hash {
    size_t operator()(Ty val) const;
};
```

## <a name="remarks"></a>Notes

L’objet de fonction définit une fonction de hachage appropriée pour mapper des valeurs de type *Ty* à une distribution de valeurs d’index. Le membre `operator()` retourne un code de hachage pour *val*, pouvant être utilisé avec les classes de modèle `unordered_map`, `unordered_multimap`, `unordered_set` et `unordered_multiset`. La bibliothèque standard fournit des spécialisations pour les types de base : *Ty* peut être tout type scalaire, y compris les types pointeur et les types énumération. De plus, il existe des spécialisations pour les types de bibliothèque `string`, `wstring`, `u16string`, `u32string`, `string_view`, `wstring_view`, `u16string_view`, `u32string_view`, `bitset`, `error_code`, `error_condition`, `optional`, `shared_ptr`, `thread`, `type_index`, `unique_ptr`, `variant` et `vector<bool>`.

## <a name="example"></a>Exemple

```cpp
// std__functional__hash.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>
#include <unordered_set>

int main()
    {
    std::unordered_set<int, std::hash<int> > c0;
    c0.insert(3);
    std::cout << *c0.find(3) << std::endl;

    return (0);
    }
```

```Output
3
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<functional>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[<unordered_map>](../standard-library/unordered-map.md)<br/>
[unordered_multimap, classe](../standard-library/unordered-multimap-class.md)<br/>
[unordered_multiset, classe](../standard-library/unordered-multiset-class.md)<br/>
[<unordered_set>](../standard-library/unordered-set.md)<br/>
