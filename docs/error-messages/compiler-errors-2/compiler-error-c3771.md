---
title: "C3771 d’erreur du compilateur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3771
dev_langs:
- C++
helpviewer_keywords:
- C3771
ms.assetid: 68c23b25-7f21-4eaa-8f7e-38fda1130a69
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 65e7a7bd56096fbeec61b651ab494d82edef9c90
ms.openlocfilehash: 448bb34ce51cea50d1f1c5d61b28b13a7ea02ff8
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3771"></a>Erreur du compilateur C3771
"identifier" : déclaration friend introuvable dans la portée espace de noms la plus proche  
  
La déclaration de modèle de classe pour le modèle spécifié *identifier* est introuvable dans l’espace de noms actuel.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Assurez-vous que la déclaration de modèle de classe pour l’identificateur de modèle est définie dans l’espace de noms actuel ou que l’identificateur de modèle est un nom complet.  
  
## <a name="example"></a>Exemple  
L’exemple de code suivant déclare un modèle de classe et une fonction dans l’espace de noms `NA`, mais tente de déclarer un modèle de fonction friend dans l’espace de noms `NB`.  
  
```cpp  
// C3771.cpp   
// compile with: /c  
  
namespace NA {  
template<class T> class A {  
    void aFunction(T t) {};  
    };  
}  
// using namespace NA;  
namespace NB {  
    class X {  
        template<class T> friend void A<T>::aFunction(T); // C3771  
// try the following line instead  
//      template<class T> friend void NA::A<T>::aFunction(T);  
// or try "using namespace NA;" instead.  
    };  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
[Modèles](../../cpp/templates-cpp.md)  
