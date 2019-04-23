---
title: __noop
ms.date: 11/04/2016
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: 674b5170dd2bba7038dfe11af906e31540acd993
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59030230"
---
# <a name="noop"></a>__noop

**Section spécifique à Microsoft**

Le `__noop` intrinsèque Spécifie qu’une fonction doit être ignorée et d’analyser la liste d’arguments, mais aucun code généré pour les arguments. Il est prévu pour une utilisation dans les fonctions de débogage globaux qui acceptent un nombre variable d’arguments.

Le compilateur convertit le `__noop` intrinsèque à 0 au moment de la compilation.

## <a name="example"></a>Exemple

Le code suivant montre comment vous pouvez utiliser `__noop`.

```
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

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)