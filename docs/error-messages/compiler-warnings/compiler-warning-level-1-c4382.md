---
title: Avertissement du compilateur (niveau 1) C4382
ms.date: 11/04/2016
f1_keywords:
- C4382
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
ms.openlocfilehash: 7b8dbf77defab2a711ad931057c740193908474b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186970"
---
# <a name="compiler-warning-level-1-c4382"></a>Avertissement du compilateur (niveau 1) C4382

> levée de'*type*' : un type avec __clrcall destructeur ou un constructeur de copie ne peut être intercepté que dans le module/CLR : pure

## <a name="remarks"></a>Notes

L’option de compilateur **/clr : pure** est déconseillée dans visual studio 2015 et n’est pas prise en charge dans visual studio 2017.

En cas de compilation avec **/CLR** (not **/clr : pure**), la gestion des exceptions s’attend à ce que les fonctions membres d’un type natif soient [__cdecl](../../cpp/cdecl.md) et non [__clrcall](../../cpp/clrcall.md). Les types natifs avec des fonctions membres utilisant `__clrcall` Convention d’appel ne peuvent pas être interceptés dans un module compilé avec **/CLR**.

Si l’exception est interceptée dans un module compilé avec **/clr : pure**, vous pouvez ignorer cet avertissement.

Pour plus d'informations, consultez [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4382.

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
