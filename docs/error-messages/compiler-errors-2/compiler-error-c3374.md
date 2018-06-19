---
title: Erreur du compilateur C3374 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3374
dev_langs:
- C++
helpviewer_keywords:
- C3374
ms.assetid: 41431299-bd20-47d4-a0c8-1334dd79018b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd06f0e63ab1c467b9359c38ad77056440535aba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253890"
---
# <a name="compiler-error-c3374"></a>Erreur du compilateur C3374
impossible de récupérer l'adresse de 'function' à moins de créer une instance de délégué  
  
 L'adresse d'une fonction a été récupérée dans un autre contexte que la création d'une instance de délégué.  
  
 L'exemple suivant génère l'erreur C3374 :  
  
```  
// C3374.cpp  
// compile with: /clr  
public delegate void MyDel(int i);  
  
ref class A {  
public:  
   void func1(int i) {  
      System::Console::WriteLine("in func1 {0}", i);  
   }  
};  
  
int main() {  
   &A::func1;   // C3374  
  
   // OK  
   A ^ a = gcnew A;  
   MyDel ^ StaticDelInst = gcnew MyDel(a, &A::func1);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour définir et utiliser des délégués (C++-CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md)