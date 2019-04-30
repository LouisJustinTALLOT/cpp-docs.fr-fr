---
title: Avertissement du compilateur (niveau 1) C4561
ms.date: 11/04/2016
f1_keywords:
- C4561
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
ms.openlocfilehash: 24a3ca8b35266e93f298314f45015b7a480e2af0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397287"
---
# <a name="compiler-warning-level-1-c4561"></a>Avertissement du compilateur (niveau 1) C4561

'__fastcall' incompatible avec le « / clr' option : conversion en '\__stdcall'

Le [__fastcall](../../cpp/fastcall.md) convention d’appel de fonction ne peut pas être utilisée avec le [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) option du compilateur. Le compilateur ignore les appels à `__fastcall`. Pour résoudre cet avertissement, supprimez les appels à **__fastcall** ou compilez sans **/CLR**.

L’exemple suivant génère C4561 :

```
// C4561.cpp
// compile with: /clr /W1 /c
// processor: x86
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve
```