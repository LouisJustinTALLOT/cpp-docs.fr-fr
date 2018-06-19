---
title: __Func__ | Documents Microsoft
ms.custom: ''
ms.date: 10/19/2017
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __func__
dev_langs:
- C++
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d78a249fe5b111c17c29895edcdc3fa5ba2f27a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32413591"
---
# <a name="func"></a>__Func__

**(C ++ 11)**  L’identificateur prédéfini &#95; &#95;func&#95; &#95; est défini de manière implicite comme une chaîne qui contient le nom non qualifié et sans ornement de la fonction englobante. &#95;&#95;Func&#95; &#95; est autorisé par la norme C++ et n’est pas une extension Microsoft.

## <a name="syntax"></a>Syntaxe

```cpp
__func__
```

## <a name="return-value"></a>Valeur de retour

Retourne une valeur null se terminant par const char un tableau de caractères qui contient le nom de fonction.

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