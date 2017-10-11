---
title: Erreur du compilateur C3855 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3855
dev_langs:
- C++
helpviewer_keywords:
- C3855
ms.assetid: ed90f8c0-4154-4243-b066-493913df5727
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 76d9101fd58d419db227803d3964198523ce3630
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3855"></a>Erreur du compilateur C3855
'classe' : paramètre de type 'param' est incompatible avec la déclaration  
  
 Le compilateur a trouvé les modèle sans type ou paramètres génériques avec des noms différents. Cela peut se produire lorsqu’un paramètre de modèle spécifié dans la définition d’une spécialisation de modèle est incompatible avec sa déclaration.  
  
 L’exemple suivant génère l’erreur C3855 :  
  
```  
// C3855.cpp  
template <int N>  
struct C {  
   void f();  
};  
  
template <char N>  
void C<N>::f() {}   // C3855  
```  
  
 Résolution possible :  
  
```  
// C3855b.cpp  
// compile with: /c  
template <int N>  
struct C {  
   void f();  
};  
  
template <int N>  
void C<N>::f() {}  
```  
  
 L’erreur C3855 peut également se produire lors de l’utilisation de génériques :  
  
```  
// C3855c.cpp  
// compile with: /clr  
generic <class T>  
ref struct GC1 {  
   generic <class U>  
   ref struct GC2;  
};  
  
generic <class T>  
generic <class U>  
generic <class V>  
ref struct GC1<T>::GC2 { };   // C3855  
```  
  
 Résolution possible :  
  
```  
// C3855d.cpp  
// compile with: /clr /c  
generic <class T>  
ref struct GC1 {  
   generic <class U>  
   ref struct GC2;  
};  
  
generic <class T>  
generic <class U>  
ref struct GC1<T>::GC2 { };  
```
