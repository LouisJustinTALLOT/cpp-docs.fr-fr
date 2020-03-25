---
title: Avertissement du compilateur (niveau 1) C4561
ms.date: 11/04/2016
f1_keywords:
- C4561
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
ms.openlocfilehash: 11a1bcdc8396b1eb74121c27154b8c6c24fa92a6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162281"
---
# <a name="compiler-warning-level-1-c4561"></a>Avertissement du compilateur (niveau 1) C4561

' __fastcall’incompatible avec l’option'/CLR' : conversion en'\__stdcall'

La Convention d’appel de fonction [__fastcall](../../cpp/fastcall.md) ne peut pas être utilisée avec l’option de compilateur [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) . Le compilateur ignore les appels à `__fastcall`. Pour résoudre cet avertissement, supprimez les appels à **__fastcall** ou compilez sans **/CLR**.

L’exemple suivant génère l’C4561 :

```cpp
// C4561.cpp
// compile with: /clr /W1 /c
// processor: x86
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve
```
