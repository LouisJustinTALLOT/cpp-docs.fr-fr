---
description: 'En savoir plus sur : __noop'
title: __noop
ms.date: 09/02/2019
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: 4b140141e0f773f01cd666dd67f77244d7aef8a5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222461"
---
# <a name="__noop"></a>__noop

**Spécifique à Microsoft**

L' **`__noop`** intrinsèque spécifie qu’une fonction doit être ignorée. La liste d’arguments est analysée, mais aucun code n’est généré pour les arguments. Elle est destinée à être utilisée dans les fonctions de débogage globales qui acceptent un nombre variable d’arguments.

Le compilateur convertit le **`__noop`** intrinsèque en 0 au moment de la compilation.

## <a name="example"></a>Exemple

Le code suivant montre comment utiliser **`__noop`** .

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

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Mots clés](../cpp/keywords-cpp.md)
