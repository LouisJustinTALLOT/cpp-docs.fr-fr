---
title: Erreur du compilateur C3214 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3214
dev_langs:
- C++
helpviewer_keywords:
- C3214
ms.assetid: 49ee4a9a-2549-4adb-9d3a-38e154303c2e
caps.latest.revision: 7
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
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 935e22f03d142531fbce9bc31d41b68726dda03a
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3214"></a>Erreur du compilateur C3214
'type' : argument de type non valide pour le paramètre générique 'paramètre' du générique 'type_générique', ne satisfait pas la contrainte 'contrainte'  
  
 Le type a été spécifié pour une instanciation d’une classe générique qui ne satisfait pas à la contrainte de la classe générique.  
  
 L’exemple suivant génère l’erreur C3214 :  
  
```  
// C3214.cpp  
// compile with: /clr  
interface struct A {};  
  
generic <class T>   
where T : A  
ref class C {};  
  
ref class X : public A {};  
  
int main() {  
   C<int>^ c = new C<int>;   // C3214  
   C<X ^> ^ c2 = new C<X^>;   // OK  
}  
```
