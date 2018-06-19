---
title: Erreur du compilateur C3642 | Documents Microsoft
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
ms.openlocfilehash: c9e841bcc4fbcb62d6a2d1e6f51f47a73bd2e06a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33264515"
---
# <a name="compiler-error-c3642"></a>Erreur du compilateur C3642
' return_type/args' : Impossible d’appeler une fonction avec la convention d’appel de code natif __clrcall  
  
 Une fonction qui est marquée avec la [__clrcall](../../cpp/clrcall.md) convention d’appel ne peut pas être appelée à partir de code natif (non managé).  
  
 *return_type/args* est le nom de la fonction ou le type de la `__clrcall` fonction que vous essayez d’appeler.  Un type est utilisé lorsque vous appelez via un pointeur de fonction.  
  
 Pour appeler une fonction managée à partir d’un contexte natif, vous pouvez ajouter une fonction de « wrapper » qui appellera le `__clrcall` (fonction). Vous pouvez également utiliser le mécanisme de marshaling CLR ; consultez [Comment : marshaler fonction pointeurs à l’aide de PInvoke](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md) pour plus d’informations.  
  
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