---
title: Compilateur avertissement (niveau 3) C4522 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4522
dev_langs: C++
helpviewer_keywords: C4522
ms.assetid: 7065dc27-0b6c-4e68-a345-c51cdb99a20b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8bccf54eced4c410310a57d919617850d928ea06
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4522"></a>Avertissement du compilateur (niveau 3) C4522
'classe' : plusieurs opérateurs d’assignation spécifiés  
  
 La classe a plusieurs opérateurs d’assignation d’un type unique. Cet avertissement est informatif ; les constructeurs peuvent être appelées dans votre programme.  
  
 Utilisez le [avertissement](../../preprocessor/warning.md) pragma pour supprimer cet avertissement.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C4522 :.  
  
```  
// C4522.cpp  
// compile with: /EHsc /W3  
#include <iostream>  
  
using namespace std;  
class A {  
public:  
   A& operator=( A & o ) { cout << "A&" << endl; return *this; }  
   A& operator=( const A &co ) { cout << "const A&" << endl; return *this; }   // C4522  
};  
  
int main() {  
   A o1, o2;  
   o2 = o1;  
   const A o3;  
   o1 = o3;  
}  
```