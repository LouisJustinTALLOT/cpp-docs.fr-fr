---
description: 'En savoir plus sur : erreur du compilateur C3821'
title: Erreur du compilateur C3821
ms.date: 11/04/2016
f1_keywords:
- C3821
helpviewer_keywords:
- C3821
ms.assetid: 2b327c7a-5faf-443c-ae82-944fae25b4df
ms.openlocfilehash: 745efeb21933e06f65f9e700ad5780da8234da90
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249371"
---
# <a name="compiler-error-c3821"></a>Erreur du compilateur C3821

'fonction' : impossible d’utiliser un type ou une fonction managée dans une fonction non managée

Les fonctions avec un assembly inline ou [setjmp](../../c-runtime-library/reference/setjmp.md) ne peuvent pas contenir de types valeur ou de classes managées. Pour corriger cette erreur, supprimez l’assembly inline et `setjmp` ou supprimez les objets managés.

C3821 peut également se produire si vous essayez d’utiliser le stockage automatique dans une fonction vararg.  Pour plus d’informations, consultez [listes d’arguments de variables (...) (C++/CLI)](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md) et [sémantique de pile C++ pour les types référence](../../dotnet/cpp-stack-semantics-for-reference-types.md).

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C3821.

```cpp
// C3821a.cpp
// compile with: /clr /c
public ref struct R {};
void test1(...) {
   R r;   // C3821
}
```

L’exemple suivant génère l’C3821.

```cpp
// C3821b.cpp
// compile with: /clr
// processor: /x86
ref class A {
   public:
   int i;
};

int main() {
   // cannot use managed classes in this function
   A ^a;

   __asm {
      nop
   }
} // C3821
```
