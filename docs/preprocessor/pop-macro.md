---
title: pop_macro
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.pop_macro
- pop_macro_CPP
helpviewer_keywords:
- pop_macro pragma
- pragmas, pop_macro
ms.assetid: 3b5489d0-69ba-4c66-b572-2748af0f12bb
ms.openlocfilehash: 28529ad0d9204034ea25fbca3696982a38889951
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437237"
---
# <a name="popmacro"></a>pop_macro
Définit la valeur de la *macro_name* macro à la valeur en haut de la pile pour cette macro.

## <a name="syntax"></a>Syntaxe

```
#pragma pop_macro("
macro_name
")
```

## <a name="remarks"></a>Notes

Vous devez tout d’abord émettre une [push_macro](../preprocessor/push-macro.md) pour *macro_name* avant de pouvoir effectuer un **pop_macro**.

## <a name="example"></a>Exemple

```cpp
// pragma_directives_pop_macro.cpp
// compile with: /W1
#include <stdio.h>
#define X 1
#define Y 2

int main() {
   printf("%d",X);
   printf("\n%d",Y);
   #define Y 3   // C4005
   #pragma push_macro("Y")
   #pragma push_macro("X")
   printf("\n%d",X);
   #define X 2   // C4005
   printf("\n%d",X);
   #pragma pop_macro("X")
   printf("\n%d",X);
   #pragma pop_macro("Y")
   printf("\n%d",Y);
}
```

```Output
1
2
1
2
1
3
```

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)