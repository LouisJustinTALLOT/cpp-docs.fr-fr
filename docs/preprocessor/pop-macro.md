---
description: 'En savoir plus sur : pragma pop_macro'
title: pop_macro, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.pop_macro
- pop_macro_CPP
helpviewer_keywords:
- pop_macro pragma
- pragmas, pop_macro
ms.assetid: 3b5489d0-69ba-4c66-b572-2748af0f12bb
ms.openlocfilehash: 395e107586b9534b2e9db616f30ddd88b15b93ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325704"
---
# <a name="pop_macro-pragma"></a>pop_macro, pragma

Affecte à la valeur de la macro de *nom de macro* la valeur en haut de la pile pour cette macro.

## <a name="syntax"></a>Syntaxe

> **#pragma pop_macro (** "*macro-Name*" **)**

## <a name="remarks"></a>Notes

Vous devez émettre une [push_macro](../preprocessor/push-macro.md) pour *macro-Name* pour pouvoir effectuer une **pop_macro**.

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

[Directives Pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
