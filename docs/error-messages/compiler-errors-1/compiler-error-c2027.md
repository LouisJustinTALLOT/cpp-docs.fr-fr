---
title: Erreur du compilateur C2027 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2027
dev_langs:
- C++
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be3c85d2ffbd3fffe4e1e6ce6dafc615f199c00a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167442"
---
# <a name="compiler-error-c2027"></a>Erreur du compilateur C2027
utilisation d’un type non défini 'type'  
  
 Un type ne peut pas être utilisé tant qu’elle est définie. Pour résoudre cette erreur, assurez-vous que le type est entièrement défini avant de le référencer.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C2027.  
  
```  
// C2027.cpp  
class C;  
class D {  
public:  
   void func() {  
   }  
};  
  
int main() {  
   C *pC;  
   pC->func();   // C2027  
  
   D *pD;  
   pD->func();  
}  
```  
  
## <a name="example"></a>Exemple  
 Il est possible de déclarer un pointeur vers un type déclaré mais pas défini.  Mais Visual C++ n’autorise pas une référence à un type non défini.  
  
 L’exemple suivant génère C2027.  
  
```  
// C2027_b.cpp  
class A;  
A& CreateA();  
  
class B;  
B* CreateB();  
  
int main() {  
   CreateA();   // C2027  
   CreateB();   // OK  
}  
```