---
description: 'En savoir plus sur l’intrinsèque Microsoft C/C++ : __noop'
title: __noop
ms.date: 12/16/2020
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: 5fd300ca8d68305a12e6b5540be05aa60a042a44
ms.sourcegitcommit: 387ce22a3b0137f99cbb856a772b5a910c9eba99
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97645083"
---
# `__noop`

L’intrinsèque **spécifique à Microsoft** **`__noop`** spécifie qu’une fonction doit être ignorée. La liste d’arguments est analysée, mais aucun code n’est généré pour les arguments. Le compilateur considère les arguments comme étant référencés dans le cadre de l’avertissement du compilateur C4100 et de l’analyse similaire. L' `__noop` intrinsèque est destiné à être utilisé dans les fonctions de débogage globales qui acceptent un nombre variable d’arguments.

Le compilateur convertit le **`__noop`** intrinsèque en 0 au moment de la compilation.

## <a name="example"></a>Exemple

Le code suivant montre comment utiliser **`__noop`** .

```cpp
// compiler_intrinsics__noop.cpp
// compile using: cl /EHsc /W4 compiler_intrinsics__noop.cpp
// compile with or without /DDEBUG
#include <stdio.h>

#if DEBUG
   #define PRINT   printf_s
#else
   #define PRINT   __noop
#endif

#define IGNORE(x) { __noop(x); }

int main(int argv, char ** argc)
{
   IGNORE(argv);
   IGNORE(argc);
   PRINT("\nDEBUG is defined\n");
}
```

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Mots clés](../cpp/keywords-cpp.md)
