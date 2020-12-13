---
description: 'En savoir plus sur : expressions lambda constexpr en C++'
title: constexpr expressions lambda en C++
ms.date: 04/08/2019
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
ms.openlocfilehash: 4ff4b3acf4289a74f8b7320620601e0e2284d356
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333939"
---
# <a name="constexpr-lambda-expressions-in-c"></a>constexpr expressions lambda en C++

**Visual Studio 2017 version 15,3 et versions ultérieures** (disponibles avec [/std : c++ 17](../build/reference/std-specify-language-standard-version.md)) : une expression lambda peut être déclarée comme **`constexpr`** ou utilisée dans une expression constante lorsque l’initialisation de chaque membre de données qu’elle capture ou introduit est autorisée dans une expression constante.

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

Une expression lambda est implicitement **`constexpr`** si son résultat satisfait aux exigences d’une **`constexpr`** fonction :

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

Si une expression lambda est implicitement ou explicitement **`constexpr`** , et que vous la Convertissez en pointeur de fonction, la fonction résultante est également **`constexpr`** :

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Objets de fonction dans la bibliothèque C++ standard](../standard-library/function-objects-in-the-stl.md)<br/>
[Appel de fonction](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)
