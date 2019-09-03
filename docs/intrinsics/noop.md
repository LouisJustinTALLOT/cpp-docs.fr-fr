---
title: __noop
ms.date: 09/02/2019
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: 24ba85b1fbbba4491c03d5a81afae345228db3bd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217186"
---
# <a name="__noop"></a>__noop

**Section spécifique à Microsoft**

L' `__noop` intrinsèque spécifie qu’une fonction doit être ignorée. La liste d’arguments est analysée, mais aucun code n’est généré pour les arguments. Elle est destinée à être utilisée dans les fonctions de débogage globales qui acceptent un nombre variable d’arguments.

Le compilateur convertit `__noop` le intrinsèque en 0 au moment de la compilation.

## <a name="example"></a>Exemple

Le code suivant montre comment utiliser `__noop`.

```cpp
// compiler_intrinsics__noop.cpp
// compile with or without /DDEBUG
#include <stdio.h>

#if DEBUG
   #define PRINT   printf_s
#else
   #define PRINT   __noop
#endif

int main() {
   PRINT("\nhello\n");
}
```

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Mots clés](../cpp/keywords-cpp.md)
