---
description: 'En savoir plus sur : classe is_placeholder'
title: is_placeholder, classe
ms.date: 11/04/2016
f1_keywords:
- functional/std::is_placeholder
helpviewer_keywords:
- is_placeholder class
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
ms.openlocfilehash: 84d73da6ffe2446a8448b0ff5f30604d259493b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230651"
---
# <a name="is_placeholder-class"></a>is_placeholder, classe

Teste si le type est un espace réservé.

## <a name="syntax"></a>Syntaxe

struct is_placeholder {valeur static const int ;};

## <a name="remarks"></a>Notes

La valeur de constante `value` est 0 si le type `Ty` n’est pas un espace réservé ; sinon, sa valeur est la position de l’argument d’appel de fonction auquel elle est liée. Vous pouvez l’utiliser pour déterminer la valeur `N` du nième espace réservé `_N`.

## <a name="example"></a>Exemple

```cpp
// std__functional__is_placeholder.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

using namespace std::placeholders;

template<class Expr>
void test_for_placeholder(const Expr&)
{
    std::cout << std::is_placeholder<Expr>::value << std::endl;
}

int main()
{
    test_for_placeholder(3.0);
    test_for_placeholder(_3);

    return (0);
}
```

```Output
0
3
```
