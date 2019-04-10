---
title: expressions lambda de constexpr en C++
ms.date: 04/08/2019
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
ms.openlocfilehash: d1bc60a6da813e54c857da38b0164f544216be00
ms.sourcegitcommit: 39debf8c525c3951af6913ee5e514617658f8859
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59424181"
---
# <a name="constexpr-lambda-expressions-in-c"></a>expressions lambda de constexpr en C++

**Visual Studio 2017 15.3 et versions ultérieures** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) : Une expression lambda peut être déclarée comme **constexpr** ou utilisées dans une expression constante lors de l’initialisation de chaque membre de données qu’elle capture ou introduit est autorisée dans une expression constante.

```cpp
    int y = 32;
    auto answer = [y]() constexpr
    {
        int x = 10;
        return y + x;
    };

    constexpr int Increment(int n)
    {
        return [n] { return n + 1; }();
    }
```

Une expression lambda est implicitement **constexpr** si son résultat satisfait aux exigences d’un **constexpr** (fonction) :

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

Si une expression lambda est implicitement ou explicitement **constexpr**et vous la convertir en un pointeur de fonction, la fonction qui en résulte est également **constexpr**:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="see-also"></a>Voir aussi

[Référence du langage C++](../cpp/cpp-language-reference.md)<br/>
[Objets de fonction dans la bibliothèque C++ Standard](../standard-library/function-objects-in-the-stl.md)<br/>
[Appel de fonction](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)