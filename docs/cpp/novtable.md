---
title: novtable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- novtable_cpp
dev_langs:
- C++
helpviewer_keywords:
- novtable __declspec keyword
- __declspec keyword [C++], novtable
ms.assetid: cfef09c5-8c1e-4b14-8a72-7d726ded4484
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5deee0209866580afd038fbce068a9275f5b5874
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406966"
---
# <a name="novtable"></a>novtable
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 Il s’agit d’un **__declspec** attributs étendus.  
  
 Cette forme de **__declspec** peut être appliqué à toute déclaration de classe, mais ne doit être appliquée qu’aux classes d’interface pures, autrement dit, les classes qui ne seront jamais instanciées sur leurs propres. Le **__declspec** arrête la génération de code pour initialiser le vfptr dans l’et le destructeur de la classe par le compilateur. Dans de nombreux cas, cela supprime les seules références à la vtable qui sont associés à la classe et, par conséquent, l'éditeur de liens supprimera cette vtable. À l’aide de cette forme de **__declspec** peut entraîner une réduction significative de la taille du code.  
  
 Si vous essayez d’instancier une classe marquée avec **novtable** et ensuite accéder à un membre de classe, vous recevrez une violation d’accès (AV).  
  
## <a name="example"></a>Exemple  
  
```cpp 
// novtable.cpp  
#include <stdio.h>  
  
struct __declspec(novtable) X {  
   virtual void mf();  
};  
  
struct Y : public X {  
   void mf() {  
      printf_s("In Y\n");  
   }  
};  
  
int main() {  
   // X *pX = new X();  
   // pX->mf();   // Causes a runtime access violation.  
  
   Y *pY = new Y();  
   pY->mf();  
}  
```  
  
```Output  
In Y  
```  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [__declspec](../cpp/declspec.md)   
 [Mots clés](../cpp/keywords-cpp.md)