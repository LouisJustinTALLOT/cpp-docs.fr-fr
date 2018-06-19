---
title: Erreur du compilateur C2797 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2797
dev_langs:
- C++
helpviewer_keywords:
- C2797
ms.assetid: 9fb26d35-eb5c-46fc-9ff5-756fba5bdaff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ea98ab3e6aed4f683fcedad144582e8e946f6d59
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33238161"
---
# <a name="compiler-error-c2797"></a>Erreur du compilateur C2797
(Obsolète) L’initialisation de listes à l’intérieur de la liste des initialiseurs membre ou l’initialiseur de membre de données non statiques n’est pas implémentée.  
  
 Cet avertissement est obsolète dans Visual Studio 2015. Dans Visual Studio 2013 et versions antérieures, le compilateur Visual C++ n’implémente pas l’initialisation de la liste dans une liste d’initialiseurs de membre ou d’un initialiseur de membre de données non statiques. Avant Visual Studio 2013 Update 3, une conversion en appel de fonction se produisait en mode silencieux, ce qui pouvait occasionner une génération de code incorrect. Visual Studio 2013 Update 3 signale cela comme une erreur.  
  
 Cet exemple génère C2797 :  
  
```  
#include <vector>  
struct S {  
    S() : v1{1} {} // C2797, VS2013 RTM incorrectly calls 'vector(size_type)'  
  
    std::vector<int> v1;  
    std::vector<int> v2{1, 2}; // C2797, VS2013 RTM incorrectly calls 'vector(size_type, const int &)'  
};  
  
```  
  
 Cet exemple génère aussi C2797 :  
  
```  
struct S1 {  
    int i;  
};  
  
struct S2 {  
    S2() : s1{0} {} // C2797, VS2013 RTM interprets as S2() : s1(0) {} causing C2664  
    S1 s1;  
    S1 s2{0}; // C2797, VS2013 RTM interprets as S1 s2 = S1(0); causing C2664  
};  
  
```  
  
 Pour résoudre ce problème, vous pouvez utiliser une construction explicite de listes internes. Par exemple :  
  
```  
#include <vector>  
typedef std::vector<int> Vector;  
struct S {  
    S() : v1(Vector{1}) {}  
  
    Vector v1;  
    Vector v2 = Vector{1, 2};  
};  
  
```  
  
 Si vous n'avez pas besoin de l'initialisation de la liste :  
  
```  
struct S {  
    S() : s1("") {}  
  
    std::string s1;  
    std::string s2 = std::string("");  
};  
  
```  
  
 (Le compilateur de Visual Studio 2013 effectue cette tâche implicitement avant Visual Studio 2013 Update 3.)