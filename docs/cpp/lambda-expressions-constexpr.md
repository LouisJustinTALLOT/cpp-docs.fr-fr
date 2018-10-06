---
title: expressions lambda de constexpr dans C++ | Microsoft Docs
ms.custom: ''
ms.date: 07/19/2017
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71c28ab1531c2af19f2b8f594db457d0272b0664
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820358"
---
# <a name="constexpr-lambda-expressions-in-c"></a>expressions lambda de constexpr en C++

**Visual Studio 2017 15.3 et versions ultérieures** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) : une expression lambda peut être déclarée comme **constexpr** ou utilisé dans une expression de l’obtention de surfaces lors de l’initialisation de chaque membre de données qu’elle capture ou introduit est autorisée dans une expression constante.

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

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Objets de fonction dans la bibliothèque standard C++](../standard-library/function-objects-in-the-stl.md)<br/>
[Appel de fonction ](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)