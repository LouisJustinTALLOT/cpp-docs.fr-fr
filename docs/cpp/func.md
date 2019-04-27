---
title: __func__
ms.date: 10/19/2017
f1_keywords:
- __func__
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
ms.openlocfilehash: eecd3efea6239c92a8bc81c0ed13a9563e5b87d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154293"
---
# <a name="func"></a>__func__

**(C ++ 11)**  L’identificateur prédéfini &#95; &#95;func&#95; &#95; est implicitement défini en tant que chaîne qui contient le nom non qualifié et de la fonction englobante. &#95;&#95;Func&#95; &#95; est autorisé par la norme C++ et n’est pas une extension Microsoft.

## <a name="syntax"></a>Syntaxe

```cpp
__func__
```

## <a name="return-value"></a>Valeur de retour

Retourne une valeur null se terminant par const char tableau de caractères qui contient le nom de fonction.

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

## <a name="requirements"></a>Configuration requise

C++11