---
title: Erreur du compilateur C2952 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2952
dev_langs:
- C++
helpviewer_keywords:
- C2952
ms.assetid: a40e18a2-d02c-4511-854f-6c6fd6789a1a
caps.latest.revision: 9
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 06d63a5d5dc308fc8616550220d706085cb44c5c
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2952"></a>Erreur du compilateur C2952
'déclaration' : la liste de paramètres est absente de la déclaration de type  
  
 Une déclaration de modèle est incorrecte.  
  
 L’exemple suivant génère l’erreur C2952 :  
  
```  
// C2952.cpp  
// compile with: /c  
template <class T>  
struct S {  
   template <class T1>  
   struct S1 {  
      void f();  
   };  
};  
  
template <class T> void S<T>::S1<T>::f() {}   // C2952  
  
// OK  
template <class T>  
template <class T1>  
void S<T>::S1<T1>::f() {}  
```  
  
 L’erreur C2952 peut également se produire lors de l’utilisation de génériques :  
  
```  
// C2952b.cpp  
// compile with: /clr /c  
generic <class T>   
ref struct GC {  
   generic <class T1>   
   ref struct GC1 {  
      void f();  
   };  
};  
  
generic <class T> void GC<T>::GC1<T>::f() {}   // C2952  
  
// OK  
generic <class T>  
generic <class T1>  
void GC<T>::GC1<T1>::f() {}  
```
