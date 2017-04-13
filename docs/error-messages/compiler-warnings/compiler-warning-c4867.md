---
title: Avertissement du compilateur C4867 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4867
dev_langs:
- C++
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: bb94e24657d16b2a3eda3a770c2b6ae734c6006f
ms.openlocfilehash: a052194893db90177b88eea8f80435777ae37773
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-c4867"></a>Avertissement du compilateur C4867
'fonction' : appel de fonction pas de liste d’arguments ; Utilisez 'appel' pour créer un pointeur vers membre  
  
 Un pointeur vers une fonction membre a été correctement initialisé.  
  
 Cet avertissement peut être due à la mise en conformité du compilateur pour Visual C++ 2005 : conformité pointeur vers membre améliorée.  Le code compilé avant Visual C++ 2005 génère désormais C4867.  
  
 Cet avertissement est toujours émis en tant qu’erreur. Utilisez le [avertissement](../../preprocessor/warning.md) pragma pour désactiver cet avertissement. Pour plus d’informations sur l’erreur C4867 et MFC/ATL, consultez [_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C4867.  
  
```  
// C4867.cpp  
// compile with: /c  
class A {  
public:  
   void f(int) {}  
  
   typedef void (A::*TAmtd)(int);  
  
   struct B {  
      TAmtd p;  
   };  
  
   void g() {  
      B b = {f};   // C4867  
      B b2 = {&A::f};   // OK  
   }  
};  
```
