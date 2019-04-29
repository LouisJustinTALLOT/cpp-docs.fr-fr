---
title: is_bind_expression, classe
ms.date: 11/04/2016
f1_keywords:
- functional/std::is_bind_expression
helpviewer_keywords:
- is_bind_expression class
ms.assetid: 0715f9e9-2239-4778-a1cf-2c21f49dfd47
ms.openlocfilehash: f547b6f74a86612174cb0f510870171158678f7a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383657"
---
# <a name="isbindexpression-class"></a>is_bind_expression, classe

Teste si le type est généré en appelant `bind`.

## <a name="syntax"></a>Syntaxe

modèle<class Ty> struct is_bind_expression {static const valeur bool ;} ;

## <a name="remarks"></a>Notes

Le membre de constante `value` a la valeur true si le type `Ty` est un type retourné par un appel à `bind` ; sinon, false.

## <a name="example"></a>Exemple

```cpp
// std__functional__is_bind_expression.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

void square(double x)
{
    std::cout << x << "^2 == " << x * x << std::endl;
}

template<class Expr>
void test_for_bind(const Expr&)
{
    std::cout << std::is_bind_expression<Expr>::value << std::endl;
}

int main()
{
    test_for_bind(3.0 * 3.0);
    test_for_bind(std::bind(square, 3));

    return (0);
}
```

```Output
0
1
```

## <a name="requirements"></a>Configuration requise

**En-tête :** \<functional>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[bind](../standard-library/functional-functions.md#bind)<br/>
