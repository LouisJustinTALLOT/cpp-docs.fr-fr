---
title: Erreur du compilateur C3642
ms.date: 11/04/2016
f1_keywords:
- C3642
helpviewer_keywords:
- C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
ms.openlocfilehash: 7c3f9f05bf04c9a1c20fff7910836e7b50468a8e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742455"
---
# <a name="compiler-error-c3642"></a>Erreur du compilateur C3642

'return_type/args' : impossible d’appeler une fonction avec __clrcall Convention d’appel à partir du code natif

Une fonction marquée avec la Convention d’appel [__clrcall](../../cpp/clrcall.md) ne peut pas être appelée à partir du code natif (non managé).

*return_type/args* est soit le nom de la fonction, soit le type de la fonction `__clrcall` que vous essayez d’appeler.  Un type est utilisé lorsque vous appelez à l’aide d’un pointeur de fonction.

Pour appeler une fonction managée à partir d’un contexte natif, vous pouvez ajouter une fonction « wrapper » qui appellera la fonction `__clrcall`. Ou vous pouvez utiliser le mécanisme de marshaling du CLR. Pour plus d’informations, consultez [Comment : marshaler des pointeurs de fonction à l’aide de PInvoke](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md) .

L’exemple suivant génère l’C3642 :

```cpp
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
