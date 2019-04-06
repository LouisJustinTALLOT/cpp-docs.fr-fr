---
title: Macros Variadic
ms.date: 11/04/2016
helpviewer_keywords:
- variadic macros [C++]
- __VA_ARGS__ variadic macro specifier
ms.assetid: 51e757dc-0134-4bb2-bb74-64ea5ad75134
ms.openlocfilehash: da159ef979ccc38845064debebae55356bc9e9bd
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59022838"
---
# <a name="variadic-macros"></a>Macros Variadic

Macros Variadic sont des macros de type fonction qui contiennent un nombre variable d’arguments.

## <a name="remarks"></a>Notes

Pour utiliser des macros variadiques, les points de suspension peut être spécifiée comme argument formel final dans une définition de macro et l’identificateur de remplacement `__VA_ARGS__` peut être utilisé dans la définition pour insérer les arguments en trop.  `__VA_ARGS__` est remplacé par tous les arguments qui correspondent aux points de suspension, y compris des virgules entre eux.

La norme du C Spécifie qu’au moins un argument doit être transmis aux points de suspension, pour vous assurer que la macro ne résout pas à une expression avec une virgule de fin.  L’implémentation Visual C++ permet de supprimer une virgule de fin si aucun argument pour les points de suspension.

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