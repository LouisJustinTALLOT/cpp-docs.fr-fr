---
title: __noop
ms.date: 09/02/2019
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: aec4df98413bf34ac1e2966d012bb905edd4775e
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857929"
---
# <a name="__noop"></a>__noop

**Section spécifique de Microsoft**

L’intrinsèque `__noop` spécifie qu’une fonction doit être ignorée. La liste d’arguments est analysée, mais aucun code n’est généré pour les arguments. Elle est destinée à être utilisée dans les fonctions de débogage globales qui acceptent un nombre variable d’arguments.

Le compilateur convertit le `__noop` intrinsèque en 0 au moment de la compilation.

## <a name="example"></a>Exemple

Le code suivant montre comment vous pouvez utiliser `__noop`.

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

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Mots clés](../cpp/keywords-cpp.md)
