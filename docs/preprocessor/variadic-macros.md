---
description: En savoir plus sur les macros variadiques
title: Variadiques, macros
ms.date: 10/17/2019
helpviewer_keywords:
- variadic macros [C++]
- __VA_ARGS__ variadic macro specifier
ms.assetid: 51e757dc-0134-4bb2-bb74-64ea5ad75134
ms.openlocfilehash: 74bf5b68696499ea8b1d88722d8a9e55f2ecab2d
ms.sourcegitcommit: 48b897797b3132ae934b1d191e3870c3c2466335
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97514590"
---
# <a name="variadic-macros"></a>Variadiques, macros

Les macros variadiques sont des macros de type fonction qui contiennent un nombre variable d’arguments.

## <a name="remarks"></a>Notes

Pour utiliser les macros variadiques, les points de suspension peuvent être spécifiés comme argument formel final dans une définition de macro, et l’identificateur de remplacement `__VA_ARGS__` peut être utilisé dans la définition pour insérer les arguments supplémentaires.  `__VA_ARGS__` est remplacé par tous les arguments qui correspondent aux points de suspension, y compris les virgules entre eux.

La norme C spécifie qu’au moins un argument doit être passé aux points de suspension pour s’assurer que la macro n’est pas résolue en une expression avec une virgule de fin. L’implémentation traditionnelle de Microsoft C++ supprime une virgule de fin si aucun argument n’est passé aux points de suspension. Lorsque l' [`/Zc:preprocessor`](../build/reference/zc-preprocessor.md) option de compilateur est définie, la virgule de fin n’est pas supprimée.

## <a name="example"></a>Exemple

```cpp
// variadic_macros.cpp
#include <stdio.h>
#define EMPTY

#define CHECK1(x, ...) if (!(x)) { printf(__VA_ARGS__); }
#define CHECK2(x, ...) if ((x)) { printf(__VA_ARGS__); }
#define CHECK3(...) { printf(__VA_ARGS__); }
#define MACRO(s, ...) printf(s, __VA_ARGS__)

int main() {
    CHECK1(0, "here %s %s %s", "are", "some", "varargs1(1)\n");
    CHECK1(1, "here %s %s %s", "are", "some", "varargs1(2)\n");   // won't print

    CHECK2(0, "here %s %s %s", "are", "some", "varargs2(3)\n");   // won't print
    CHECK2(1, "here %s %s %s", "are", "some", "varargs2(4)\n");

    // always invokes printf in the macro
    CHECK3("here %s %s %s", "are", "some", "varargs3(5)\n");

    MACRO("hello, world\n");

    MACRO("error\n", EMPTY); // would cause error C2059, except VC++
                             // suppresses the trailing comma
}
```

```Output
here are some varargs1(1)
here are some varargs2(4)
here are some varargs3(5)
hello, world
error
```

## <a name="see-also"></a>Voir aussi

[Macros (C/C++)](../preprocessor/macros-c-cpp.md)
