---
title: Compilateur avertissement (niveau 1) C4382 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4382
dev_langs:
- C++
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29afe066fb86d0dd99216a63c057046ec76de55b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704319"
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