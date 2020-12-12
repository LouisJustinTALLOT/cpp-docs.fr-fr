---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4703'
title: Avertissement du compilateur (niveau 4) C4703
ms.date: 11/04/2016
f1_keywords:
- C4703
helpviewer_keywords:
- C4703
ms.assetid: 5dad454e-69e3-4931-9168-050a861c05f8
ms.openlocfilehash: 8c31ed9be7dc271f9de4471792ccd6517091cab6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97133781"
---
# <a name="compiler-warning-level-4-c4703"></a>Avertissement du compilateur (niveau 4) C4703

Variable de pointeur local potentiellement non initialisée’nom’utilisée

Le *nom* de la variable de pointeur local a peut-être été utilisé sans qu’une valeur lui ait été assignée. Cela peut entraîner des résultats imprévisibles.

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

int main()
{
    func(9);
}
```

```Output
c:\src\test.cpp(10) : warning C4701: potentially uninitialized local variable 'p' used
c:\src\test.cpp(10) : warning C4703: potentially uninitialized local pointer variable 'p' used
```

Pour corriger cet avertissement, initialisez la variable comme indiqué dans l’exemple suivant :

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

int main()
{
    func(9);
}
```

## <a name="see-also"></a>Voir aussi

[Avertissement du compilateur (niveau 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)<br/>
[Avertissements,/SDL et amélioration de la détection des variables non initialisées](https://www.microsoft.com/security/blog/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/)
