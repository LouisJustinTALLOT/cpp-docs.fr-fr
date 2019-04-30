---
title: Avertissement du compilateur (niveau 1) C4382
ms.date: 11/04/2016
f1_keywords:
- C4382
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
ms.openlocfilehash: cca2f8cc13cc8317bac3736e142ef58e126ed994
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390488"
---
# <a name="compiler-warning-level-1-c4382"></a>Avertissement du compilateur (niveau 1) C4382

> lever '*type*' : un type avec le constructeur de copie ou le destructeur __clrcall ne peut être intercepté que dans/CLR : pure module

## <a name="remarks"></a>Notes

Le **/CLR : pure** option du compilateur est déconseillée dans Visual Studio 2015 et non pris en charge dans Visual Studio 2017.

Lors de la compilation avec **/CLR** (pas **/CLR : pure**), la gestion des exceptions attend les fonctions membres dans un type natif soient [__cdecl](../../cpp/cdecl.md) et non [__clrcall](../../cpp/clrcall.md). Les types natifs avec des fonctions de membre à l’aide de `__clrcall` convention d’appel ne peut pas être interceptée dans un module compilé avec **/CLR**.

Si l’exception est interceptée dans un module compilé avec **/CLR : pure**, vous pouvez ignorer cet avertissement.

Pour plus d’informations, consultez l’article [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C4382.

```cpp
// C4382.cpp
// compile with: /clr /W1 /c
struct S {
   __clrcall ~S() {}
};

struct T {
   ~T() {}
};

int main() {
   S s;
   throw s;   // C4382

   S * ps = &s;
   throw ps;   // OK

   T t;
   throw t;   // OK
}
```