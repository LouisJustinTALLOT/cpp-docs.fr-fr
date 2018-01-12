---
title: Compilateur avertissement (niveau 3) C4521 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4521
dev_langs: C++
helpviewer_keywords: C4521
ms.assetid: 057d770c-ebcf-44cd-b943-1b1bb1ceaa8c
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cb06f8d2cdbc29f5c6f98dfaeb23eeffe1167ef8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4521"></a>Avertissement du compilateur (niveau 3) C4521
'classe' : plusieurs constructeurs de copie spécifiés  
  
 La classe a plusieurs constructeurs de copie d’un type unique. Cet avertissement est informatif ; les constructeurs peuvent être appelées dans votre programme.  
  
 Utilisez le [avertissement](../../preprocessor/warning.md) pragma pour supprimer cet avertissement.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C4521 :.  
  
```  
// C4521.cpp  
// compile with: /EHsc /W3  
#include <iostream>  
  
using namespace std;  
class A {  
public:  
   A() { cout << "A's default constructor" << endl; }  
   A( A &o ) { cout << "A&" << endl; }  
   A( const A &co ) { cout << "const A&" << endl; }   // C4521  
};  
  
int main() {  
   A o1;         // Calls default constructor.  
   A o2( o1 );   // Calls A( A& ).  
   const A o3;   // Calls default constructor.  
   A o4( o3 );   // Calls A( const A& ).  
}  
```