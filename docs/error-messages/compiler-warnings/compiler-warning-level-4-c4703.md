---
title: Avertissement du compilateur (niveau 4) C4703
ms.date: 11/04/2016
f1_keywords:
- C4703
helpviewer_keywords:
- C4703
ms.assetid: 5dad454e-69e3-4931-9168-050a861c05f8
ms.openlocfilehash: 6115db7611de521d66df3b1f555349891d72cc03
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59025795"
---
# <a name="compiler-warning-level-4-c4703"></a>Avertissement du compilateur (niveau 4) C4703

Potentiellement non initialisée variable de pointeur locale 'name' utilisé

La variable de pointeur locale *nom* a peut-être été utilisé sans assignée une valeur. Cela peut entraîner des résultats imprévisibles.

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

[Avertissement du compilateur (niveau 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)<br/>
[Avertissements, /sdl et amélioration de la détection des variables non initialisée](https://www.microsoft.com/security/blog/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/)