---
title: Erreur du compilateur C2452 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2452
dev_langs:
- C++
helpviewer_keywords:
- C2452
ms.assetid: a4ec7642-6660-4c7a-9866-853d1cc67daf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f4d30de808600c34270c8576adb371497af169aa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197219"
---
# <a name="compiler-error-c2452"></a>Erreur du compilateur C2452
'type' : type de source non valide pour safe_cast  
  
 Le type de source [safe_cast](../../windows/safe-cast-cpp-component-extensions.md) n’était pas valide.  Par exemple, tous les types dans un `safe_cast` opération doive être des types CLR.  
  
 L’exemple suivant génère l’erreur C2452 :  
  
```  
// C2452.cpp  
// compile with: /clr  
  
struct A {};  
struct B : public A {};  
  
ref struct C {};  
ref struct D : public C{};  
  
int main() {  
   A a;  
   safe_cast<B*>(&a);   // C2452  
  
   // OK  
   C ^ c = gcnew C;  
   safe_cast<D^>(c);  
}  
```