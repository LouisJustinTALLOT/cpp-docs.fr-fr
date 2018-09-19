---
title: Erreur du compilateur C3642 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3642
dev_langs:
- C++
helpviewer_keywords:
- C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: febd6f1a9a3b4bac8bbee59cbf8c5bead93c3fb3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047718"
---
# <a name="compiler-error-c3642"></a>Erreur du compilateur C3642

' return_type/args' : Impossible d’appeler une fonction avec la convention d’appel de code natif __clrcall

Une fonction qui est marquée avec le [__clrcall](../../cpp/clrcall.md) convention d’appel ne peut pas être appelée à partir de code natif (non managé).

*return_type/args* est le nom de la fonction ou le type de la `__clrcall` fonction que vous essayez d’appeler.  Un type est utilisé lorsque vous appelez via un pointeur de fonction.

Pour appeler une fonction managée à partir d’un contexte natif, vous pouvez ajouter une fonction de « wrapper » qui appellera le `__clrcall` (fonction). Vous pouvez également utiliser le mécanisme de marshaling CLR ; consultez [Comment : marshaler des pointeurs de fonction l’utilisation de PInvoke](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md) pour plus d’informations.

L’exemple suivant génère l’erreur C3642 :

```
// C3642.cpp
// compile with: /clr
using namespace System;
struct S {
   void Test(String ^ s) {   // CLR type in signature, implicitly __clrcall
      Console::WriteLine(s);
   }
   void Test2(char * s) {
      Test(gcnew String(s));
   }
};

#pragma unmanaged
int main() {
   S s;
   s.Test("abc");   // C3642
   s.Test2("abc");   // OK
}
```