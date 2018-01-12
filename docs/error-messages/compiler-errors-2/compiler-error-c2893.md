---
title: Erreur du compilateur C2893 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2893
dev_langs: C++
helpviewer_keywords: C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d6a926b6cf935d1910681b77d95f60847205bc05
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2893"></a>Erreur du compilateur C2893
La spécialisation du modèle de fonction 'nom de modèle'  
  
 Le compilateur a échoué spécialiser un modèle de fonction. Il peut y avoir plusieurs causes pour cette erreur.  
  
 En règle générale, la pour résoudre une erreur C2893 consiste à examiner la signature de la fonction et assurez-vous que vous pouvez instancier chaque type.  
  
## <a name="example"></a>Exemple  
 Erreur C2893 se produit parce que `f`du paramètre de modèle `T` est déduit pour être `std::map<int,int>`, mais `std::map<int,int>` n’a aucun membre `data_type` (`T::data_type` ne peut pas être instancié avec `T = std::map<int,int>`.). L’exemple suivant génère l’erreur C2893.  
  
```  
// C2893.cpp  
// compile with: /c /EHsc  
#include<map>  
using namespace std;  
class MyClass {};  
  
template<class T>   
inline typename T::data_type  
// try the following line instead  
// inline typename  T::mapped_type  
f(T const& p1, MyClass const& p2);  
  
template<class T>  
void bar(T const& p1) {  
    MyClass r;  
    f(p1,r);   // C2893  
}  
  
int main() {  
   map<int,int> m;  
   bar(m);  
}  
```