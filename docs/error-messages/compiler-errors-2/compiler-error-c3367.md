---
title: Erreur du compilateur C3367 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3367
dev_langs:
- C++
helpviewer_keywords:
- C3367
ms.assetid: e675d42b-f5b0-4d43-aab1-1f5024233102
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2884e38d1ad1aecef8e7b0723674ebd9849d8f40
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257072"
---
# <a name="compiler-error-c3367"></a>Erreur du compilateur C3367
'fonction_membre_statique' : impossible d’utiliser une fonction static pour créer un délégué indépendant  
  
Quand vous appelez un délégué indépendant, vous devez passer une instance d’un objet. Dans la mesure où une fonction membre statique est appelée par le nom de classe, vous ne pouvez instancier un délégué indépendant qu’avec une fonction membre d’instance.  
  
Pour plus d’informations sur les délégués indépendants, consultez [Comment : définir et utiliser délègue (C + c++ / CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md).  
  
## <a name="example"></a>Exemple  
L’exemple suivant génère l’erreur C3367.  
  
```cpp  
// C3367.cpp  
// compile with: /clr  
ref struct R {  
   void b() {}  
   static void f() {}  
};  
  
delegate void Del(R^);  
  
int main() {  
   Del ^ a = gcnew Del(&R::b);   // OK  
   Del ^ b = gcnew Del(&R::f);   // C3367  
}  
```