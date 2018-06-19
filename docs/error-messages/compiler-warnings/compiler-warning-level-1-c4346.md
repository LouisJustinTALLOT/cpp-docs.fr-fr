---
title: Compilateur avertissement (niveau 1) C4346 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4346
dev_langs:
- C++
helpviewer_keywords:
- C4346
ms.assetid: 68ee562d-cca9-4a2a-9a1b-14ad1a1e7396
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 090c7ba576973c2dfb2e5fd7e117cddc379b4dfe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276261"
---
# <a name="compiler-warning-level-1-c4346"></a>Avertissement du compilateur (niveau 1) C4346
'nom' : nom dépendant n’est pas un type  
  
 Le [typename](../../cpp/typename.md) mot clé est obligatoire si un nom dépendant est traitée comme un type. Pour le code qui est identique dans toutes les versions de Visual C++, ajoutez `typename` à la déclaration.  
  
 L’exemple suivant génère l’erreur C4346 :  
  
```  
// C4346.cpp  
// compile with: /WX /LD  
template<class T>  
struct C {  
   T::X* x;   // C4346  
   // try the following line instead  
   // typename T::X* x;  
};  
```  
  
 Les exemples suivants illustrent d’autres situations où la **typename** mot clé est requise :  
  
```  
// C4346b.cpp  
// compile with: /LD /W1  
template<class T>  
const typename T::X& f(typename T::Z* p);   // Required in both places  
  
template<class T, int N>  
struct L{};  
  
template<class T>  
struct M : public L<typename T::Type, T::Value>   
{   // required on type argument, not on non-type argument  
   typedef typename T::X   Type;  
   Type f();   // OK: "Type" is a type-specifer  
   typename T::X g();   // typename required  
   operator typename T::Z();   // typename required      
};  
```  
  
 et ce,  
  
```  
// C4346c.cpp  
// compile with: /LD /WX  
struct Y {  
   typedef int Y_t;  
};  
  
template<class T>  
struct A {  
   typedef Y A_t;  
};  
  
template<class T>  
struct B {  
   typedef /*typename*/ A<T>::A_t B_t;   // C4346 typename needed here  
   typedef /*typename*/ B_t::Y_t  B_t2;   // typename also needed here  
};  
```