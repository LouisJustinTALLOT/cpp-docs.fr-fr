---
description: 'En savoir plus sur : erreur du compilateur C3642'
title: Erreur du compilateur C3642
ms.date: 11/04/2016
f1_keywords:
- C3642
helpviewer_keywords:
- C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
ms.openlocfilehash: 77d65d2bb2c426fe78671328b0eccab739b9dabe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340305"
---
# <a name="compiler-error-c3642"></a>Erreur du compilateur C3642

'return_type/args' : impossible d’appeler une fonction avec __clrcall Convention d’appel à partir du code natif

Une fonction marquée avec la Convention d’appel [__clrcall](../../cpp/clrcall.md) ne peut pas être appelée à partir du code natif (non managé).

*return_type/args* est soit le nom de la fonction, soit le type de la `__clrcall` fonction que vous essayez d’appeler.  Un type est utilisé lorsque vous appelez à l’aide d’un pointeur de fonction.

Pour appeler une fonction managée à partir d’un contexte natif, vous pouvez ajouter une fonction « wrapper » qui appellera la `__clrcall` fonction. Ou vous pouvez utiliser le mécanisme de marshaling du CLR. Pour plus d’informations, consultez [Comment : marshaler des pointeurs de fonction à l’aide de PInvoke](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md) .

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
