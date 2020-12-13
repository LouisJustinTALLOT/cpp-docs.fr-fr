---
description: 'En savoir plus sur : __Func__'
title: __func__
ms.date: 10/19/2017
f1_keywords:
- __func__
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
ms.openlocfilehash: 6e075d0f566bb8c3eb72e62a30a36ef80528647b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337702"
---
# <a name="__func__"></a>__func__

**(C++ 11)** L’identificateur prédéfini &#95;&#95;Func&#95;&#95; est implicitement défini comme une chaîne qui contient le nom non qualifié et sans ornement de la fonction englobante. &#95;&#95;Func&#95;&#95; est imposé par la norme C++ et n’est pas une extension Microsoft.

## <a name="syntax"></a>Syntaxe

```cpp
__func__
```

## <a name="return-value"></a>Valeur de retour

Retourne un tableau de caractères const, terminé par le caractère null, qui contient le nom de la fonction.

## <a name="example"></a>Exemple

```cpp
#include <string>
#include <iostream>

namespace Test
{
    struct Foo
    {
        static void DoSomething(int i, std::string s)
        {
           std::cout << __func__ << std::endl; // Output: DoSomething
        }
    };
}

int main()
{
    Test::Foo::DoSomething(42, "Hello");

    return 0;
}
```

## <a name="requirements"></a>Spécifications

C++11
