---
description: 'En savoir plus sur : erreur du compilateur C2107'
title: Erreur du compilateur C2107
ms.date: 11/04/2016
f1_keywords:
- C2107
helpviewer_keywords:
- C2107
ms.assetid: 2866a121-884e-4bb5-8613-36de5817000e
ms.openlocfilehash: aee5e7384f3d0a58265d1cc36448c7fb49c71f4f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335278"
---
# <a name="compiler-error-c2107"></a>Erreur du compilateur C2107

index non conforme, indirection non autorisée

Un indice est appliqué à une expression qui ne correspond pas à un pointeur.

## <a name="example"></a>Exemple

C2107 peut se produire si vous utilisez incorrectement le **`this`** pointeur d’un type valeur pour accéder à l’indexeur par défaut du type. Pour plus d’informations, consultez [sémantiques du pointeur this](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer).

L’exemple suivant génère l’C2107.

```cpp
// C2107.cpp
// compile with: /clr
using namespace System;

value struct B {
   property String ^ default[String ^] {
      String ^ get(String ^ data) {
         return "abc";
      }
   }
   void Test() {
      Console::WriteLine("{0}", this["aa"]);   // C2107
      Console::WriteLine("{0}", this->default["aa"]);   // OK
   }
};

int main() {
   B ^ myb = gcnew B();
   myb->Test();
}
```
