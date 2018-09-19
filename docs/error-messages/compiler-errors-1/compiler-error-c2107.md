---
title: Erreur du compilateur C2107 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2107
dev_langs:
- C++
helpviewer_keywords:
- C2107
ms.assetid: 2866a121-884e-4bb5-8613-36de5817000e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df81df38758cfdd9b3f62d9e0d241f0bf8578746
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097889"
---
# <a name="compiler-error-c2107"></a>Erreur du compilateur C2107

index non conforme, indirection interdite

Un indice est appliqué à une expression qui ne correspond pas à un pointeur.

## <a name="example"></a>Exemple

C2107 peut se produire si vous utilisez incorrectement le `this` pointeur d’un type de valeur pour l’indexeur de valeur par défaut du type d’accès. Pour plus d’informations, consultez [sémantiques de ce pointeur](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer).

L’exemple suivant génère l’erreur C2107.

```
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