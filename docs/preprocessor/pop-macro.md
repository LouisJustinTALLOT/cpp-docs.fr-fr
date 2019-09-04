---
title: pop_macro, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.pop_macro
- pop_macro_CPP
helpviewer_keywords:
- pop_macro pragma
- pragmas, pop_macro
ms.assetid: 3b5489d0-69ba-4c66-b572-2748af0f12bb
ms.openlocfilehash: f9e097d139e1df5c9ba09ad9ca99f0cfe6bbbfb3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218284"
---
# <a name="pop_macro-pragma"></a>pop_macro, pragma

Affecte à la valeur de la macro de *nom de macro* la valeur en haut de la pile pour cette macro.

## <a name="syntax"></a>Syntaxe

> **#pragma pop_macro (** "*macro-Name*" **)**

## <a name="remarks"></a>Notes

Un [push_macro](../preprocessor/push-macro.md) pour la *macro-Name* doit être émis pour que vous puissiez effectuer un **pop_macro**.

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

[Directives pragma et mot clé __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
