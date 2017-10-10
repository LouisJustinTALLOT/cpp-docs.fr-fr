---
title: Erreur du compilateur C2761 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2761
dev_langs:
- C++
helpviewer_keywords:
- C2761
ms.assetid: 38c79a05-b56d-485b-820f-95e8c0cb926f
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 7670c3fa67579c218024dfd3f1f585ad57cf37e5
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2761"></a>Erreur du compilateur C2761
'fonction' : redéclaration de la fonction membre non autorisée  
  
 Vous ne pouvez pas redéclarer une fonction membre. Vous pouvez définir, mais pas la redéclarer.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C2761 :.  
  
```  
// C2761.cpp  
class a {  
   int t;  
   void test();  
};  
  
void a::a;     // C2761  
void a::test;  // C2761  
  
```  
  
## <a name="example"></a>Exemple  
 Les membres non static d’une classe ou d’une structure ne peuvent pas être définis.  L’exemple suivant génère l’erreur C2761 :.  
  
```  
// C2761_b.cpp  
// compile with: /c  
struct C {  
   int s;  
   static int t;  
};  
  
int C::s;   // C2761  
int C::t;   // OK  
```
