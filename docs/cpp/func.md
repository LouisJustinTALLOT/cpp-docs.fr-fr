---
title: __func__
ms.date: 10/19/2017
f1_keywords:
- __func__
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
ms.openlocfilehash: 8e94caffe120c325478d8b4f24c1915a516d69f4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179820"
---
# <a name="__func__"></a>__func__

**(C++ 11)** L’identificateur &#95; &#95;prédéfini Func&#95; &#95; est défini implicitement comme une chaîne qui contient le nom non qualifié et sans ornement de la fonction englobante. &#95;&#95;Func&#95; &#95; est mandaté par la C++ norme et n’est pas une extension Microsoft.

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
