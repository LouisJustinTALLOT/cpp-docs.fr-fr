---
description: 'En savoir plus sur &lt; : &gt; opérateurs fonctionnels'
title: '&lt;functional&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- functional/std::operator!=
- functional/std::operator==
helpviewer_keywords:
- functional operators
ms.assetid: d4b3c760-f3e2-4b65-bdaa-d42e8dd6f5e1
ms.openlocfilehash: a22e9203e89c041d5ed1925d55d1cd3aa6d61ba3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324237"
---
# <a name="ltfunctionalgt-operators"></a>&lt;functional&gt;, opérateurs

## <a name="operator"></a><a name="op_eq_eq"></a> opérateur = =

Teste si l'objet pouvant être appelé est vide.

```cpp
template <class Fty>
    bool operator==(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
    bool operator==(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Paramètres

*Fty*\
Type de fonction à encapsuler.

*FA*\
Objet de function.

*NPC*\
Pointeur null.

### <a name="remarks"></a>Notes

Les opérateurs prennent tous deux un argument qui est une référence à un objet `function` et un argument qui est une constante de pointeur null. Tous deux retournent la valeur true uniquement si l'objet `function` est vide.

### <a name="example"></a>Exemple

```cpp
// std__functional__operator_eq.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
{
    return (-val);
}

int main()
{
    std::function<int(int)> fn0;
    std::cout << std::boolalpha << "empty == "
        << (fn0 == 0) << std::endl;

    std::function<int(int)> fn1(neg);
    std::cout << std::boolalpha << "empty == "
        << (fn1 == 0) << std::endl;

    return (0);
}
```

```Output
empty == true
empty == false
```

## <a name="operator"></a><a name="op_neq"></a> opérateur ! =

Vérifie si l’objet pouvant être appelé n’est pas vide.

```cpp
template <class Fty>
    bool operator!=(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
    bool operator!=(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Paramètres

*Fty*\
Type de fonction à encapsuler.

*FA*\
Objet de function.

*NPC*\
Pointeur null.

### <a name="remarks"></a>Notes

Les opérateurs prennent tous deux un argument qui est une référence à un objet `function` et un argument qui est une constante de pointeur null. Tous deux retournent la valeur true uniquement si l’objet `function` n’est pas vide.

### <a name="example"></a>Exemple

```cpp
// std__functional__operator_ne.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0;
    std::cout << std::boolalpha << "not empty == "
        << (fn0 != 0) << std::endl;

    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "not empty == "
        << (fn1 != 0) << std::endl;

    return (0);
    }
```

```Output
not empty == false
not empty == true
```
