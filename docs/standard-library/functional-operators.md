---
title: '&lt;functional&gt;, opérateurs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- functional/std::operator!=
- functional/std::operator==
dev_langs:
- C++
helpviewer_keywords:
- functional operators
ms.assetid: d4b3c760-f3e2-4b65-bdaa-d42e8dd6f5e1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e84ed8ed97a529d67c6d136fd8464cd13c8a502
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845217"
---
# <a name="ltfunctionalgt-operators"></a>&lt;functional&gt;, opérateurs

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_eq_eq"></a>  operator==

Teste si l'objet pouvant être appelé est vide.

```cpp
template <class Fty>
bool operator==(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
bool operator==(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Paramètres

`Fty` Le type de fonction à encapsuler.

`f` L’objet de fonction

`npc` Un pointeur null.

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

## <a name="op_neq"></a>  operator!=

Vérifie si l’objet pouvant être appelé n’est pas vide.

```cpp
template <class Fty>
bool operator!=(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
bool operator!=(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Paramètres

`Fty` Le type de fonction à encapsuler.

`f` L’objet de fonction

`npc` Un pointeur null.

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

## <a name="see-also"></a>Voir aussi

[\<functional>](../standard-library/functional.md)<br/>
