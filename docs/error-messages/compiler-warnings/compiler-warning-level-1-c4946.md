---
title: Compilateur avertissement (niveau 1) C4946 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4946
dev_langs:
- C++
helpviewer_keywords:
- C4946
ms.assetid: b85cbef0-e053-4de6-9b14-7b0f82d40495
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 800d940c3005762bddf6402a14af4416da4bc50e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4946"></a>Avertissement du compilateur (niveau 1) C4946
reinterpret_cast utilisé entre des classes connexes : 'classe1' et 'classe2'  
  
 N’utilisez pas [reinterpret_cast](../../cpp/reinterpret-cast-operator.md) pour effectuer un cast entre des types. Utilisez [static_cast](../../cpp/static-cast-operator.md) à la place, ou pour des types polymorphes, utilisez [dynamic_cast](../../cpp/dynamic-cast-operator.md).  
  
 Par défaut, cet avertissement est désactivé. Pour plus d'informations, consultez [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 L’exemple de code suivant génère l’erreur C4946 :  
  
```  
// C4946.cpp  
// compile with: /W1  
#pragma warning (default : 4946)  
class a {  
public:  
   a() : m(0) {}  
   int m;  
};  
  
class b : public virtual a {  
};  
  
class b2 : public virtual a {  
};  
  
class c : public b, public b2 {  
};  
  
int main() {  
   c* pC = new c;  
   a* pA = reinterpret_cast<a*>(pC);   // C4946  
   // try the following line instead  
   // a* pA = static_cast<a*>(pC);  
}  
```