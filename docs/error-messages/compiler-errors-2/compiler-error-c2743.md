---
title: Erreur du compilateur C2743
ms.date: 11/04/2016
f1_keywords:
- C2743
helpviewer_keywords:
- C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
ms.openlocfilehash: d679ce0df0d43772a6c32aa8e00869ac1a4a082b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759644"
---
# <a name="compiler-error-c2743"></a>Erreur du compilateur C2743

'type' : impossible d’intercepter un type natif avec __clrcall destructeur ou un constructeur de copie

Un module compilé avec **/CLR** a tenté d’intercepter une exception de type natif et où le destructeur ou le constructeur de copie du type utilise `__clrcall` Convention d’appel.

En cas de compilation avec **/CLR**, la gestion des exceptions s’attend à ce que les fonctions membres d’un type natif soient [__cdecl](../../cpp/cdecl.md) et non [__clrcall](../../cpp/clrcall.md). Les types natifs avec des fonctions membres utilisant `__clrcall` Convention d’appel ne peuvent pas être interceptés dans un module compilé avec **/CLR**.

Pour plus d’informations, consultez l’article [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2743.

```cpp
// C2743.cpp
// compile with: /clr
public struct S {
   __clrcall ~S() {}
};

public struct T {
   ~T() {}
};

int main() {
   try {}
   catch(S) {}   // C2743
   // try the following line instead
   // catch(T) {}

   try {}
   catch(S*) {}   // OK
}
```
