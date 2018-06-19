---
title: constexpr Expressions Lambda en C++ | Documents Microsoft
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
ms.openlocfilehash: 1e01f41aaf8b761020f57625e7cbf06f8fba2659
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418898"
---
# <a name="constexpr-lambda-expressions-in-c"></a>constexpr Expressions Lambda en C++
**Visual Studio 2017 15,3 et versions ultérieures** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) : une expression lambda peut être déclarée comme `constexpr` ou utilisée dans une expression de l’obtention de surfaces lors de l’initialisation de chaque membre de données qu’elle capture ou introduit est autorisée dans une expression constante.  

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
Une expression lambda est implicitement `constexpr` si son résultat répond aux exigences d’un `constexpr` (fonction) :
```cpp
    auto answer = [](int n) 
    {
        return 32 + n; 
    };

    constexpr int response = answer(10);
``` 
Si une expression lambda est implicitement ou explicitement `constexpr`et que vous la convertir en un pointeur de fonction, la fonction obtenue est également `constexpr`:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```
  
## <a name="see-also"></a>Voir aussi  
 [Référence du langage C++](../cpp/cpp-language-reference.md)   
 [Objets de fonction dans la bibliothèque Standard C++](../standard-library/function-objects-in-the-stl.md)   
 [Appel de fonction](../cpp/function-call-cpp.md)   
 [for_each](../standard-library/algorithm-functions.md#for_each)