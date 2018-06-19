---
title: Erreur du compilateur C2249 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2249
dev_langs:
- C++
helpviewer_keywords:
- C2249
ms.assetid: bdd6697c-e04b-49b9-8e40-d9eb6d74f2b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a4d5ab3de2a3bd04ba2a2bb9c90ebe8f04b3e67
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171449"
---
# <a name="compiler-error-c2249"></a>Erreur du compilateur C2249
'membre' : aucun chemin accessible vers membre déclaré dans la base virtuelle 'classe'  
  
 Le `member` est héritée d’un nonpublic `virtual` classe de base ou une structure.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C2249.  
  
```  
// C2249.cpp  
class A {  
private:  
   void privFunc( void ) {};  
public:  
   void pubFunc( void ) {};  
};  
  
class B : virtual public A {} b;  
  
int main() {  
   b.privFunc();    // C2249, private member of A  
   b.pubFunc();    // OK  
}  
```  
  
## <a name="example"></a>Exemple  
 C2249 peut également se produire si vous essayez d’assigner un flux de données à partir de la bibliothèque C++ Standard dans un autre flux.  L’exemple suivant génère C2249.  
  
```  
// C2249_2.cpp  
#include <iostream>  
using namespace std;  
int main() {  
   cout = cerr;   // C2249  
   #define cout cerr;   // OK  
}  
```