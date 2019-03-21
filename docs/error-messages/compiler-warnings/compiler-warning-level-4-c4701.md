---
title: Avertissement du compilateur (niveau 4) C4701
ms.date: 11/04/2016
f1_keywords:
- C4701
helpviewer_keywords:
- C4701
ms.assetid: d7c76c66-1f3f-4d3c-abe4-5d94c84a5a1f
ms.openlocfilehash: 7d9b0041428af62c4b9d7a9a170547ab75222e94
ms.sourcegitcommit: 90817d9d78fbaed8ffacde63f3add334842e596f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58278422"
---
# <a name="compiler-warning-level-4-c4701"></a>Avertissement du compilateur (niveau 4) C4701

variable locale potentiellement non initialisée 'name' utilisé

La variable locale *nom* a peut-être été utilisé sans assignée une valeur. Cela peut entraîner des résultats imprévisibles.

## <a name="example"></a>Exemple

Le code suivant génère C4701 et C4703.

```cpp
#include <malloc.h>

void func(int size)
{
    void* p;
    if (size < 256) {
        p = malloc(size);
    }

    if (p != nullptr) // C4701 and C4703
        free(p);
}

void main()
{
    func(9);
}
```

```Output
c:\src\test.cpp(10) : warning C4701: potentially uninitialized local variable 'p' used
c:\src\test.cpp(10) : warning C4703: potentially uninitialized local pointer variable 'p' used
```

Pour corriger cet avertissement, initialisez la variable comme indiqué dans cet exemple :

```cpp
#include <malloc.h>

void func(int size)
{
    void* p = nullptr;
    if (size < 256) {
        p = malloc(size);
    }

    if (p != nullptr)
        free(p);
}

void main()
{
    func(9);
}
```

## <a name="see-also"></a>Voir aussi

[Avertissement du compilateur (niveau 4) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)<br/>
[Avertissements, /sdl et amélioration de la détection des variables non initialisée](https://www.microsoft.com/security/blog/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/)