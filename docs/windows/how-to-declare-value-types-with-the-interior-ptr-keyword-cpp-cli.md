---
title: "Comment : déclarer des Types valeur avec le mot clé interior_ptr (C + c++ / CLI) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- _ptr keyword
- value types, declaring
ms.assetid: 49eea66e-eeba-49bd-95b0-ba297be436e3
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4b42cbbbc175b3d48baa7b7b2e1c1a5b0e4cbf15
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-declare-value-types-with-the-interiorptr-keyword-ccli"></a>Comment : déclarer des types de valeur avec le mot clé interior_ptr (C++/CLI)
Un `interior_ptr` peut être utilisé avec un type valeur.  
  
> [!IMPORTANT]
>  Cette fonctionnalité de langage est pris en charge par le **/CLR** option du compilateur, mais pas par le **/ZW** option du compilateur.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 C suivant + c++ / CLI montre comment utiliser un `interior_ptr` avec un type valeur.  
  
### <a name="code"></a>Code  
  
```  
// interior_ptr_value_types.cpp  
// compile with: /clr  
value struct V {  
   V(int i) : data(i){}  
   int data;  
};  
  
int main() {  
   V v(1);  
   System::Console::WriteLine(v.data);  
  
   // pointing to a value type  
   interior_ptr<V> pv = &v;  
   pv->data = 2;  
  
   System::Console::WriteLine(v.data);  
   System::Console::WriteLine(pv->data);  
  
   // pointing into a value type  
   interior_ptr<int> pi = &v.data;  
   *pi = 3;  
   System::Console::WriteLine(*pi);  
   System::Console::WriteLine(v.data);  
   System::Console::WriteLine(pv->data);  
}  
```  
  
### <a name="output"></a>Sortie  
  
```  
1  
2  
2  
3  
3  
3  
```  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 Dans un type valeur, le `this` pointeur prend la valeur interior_ptr.  
  
 Dans le corps d’une fonction membre non statique d’un type valeur `V`, `this` est une expression de type `interior_ptr<V>` dont la valeur est l’adresse de l’objet pour lequel la fonction est appelée.  
  
### <a name="code"></a>Code  
  
```  
// interior_ptr_value_types_this.cpp  
// compile with: /clr /LD  
value struct V {  
   int data;  
   void f() {  
      interior_ptr<V> pv1 = this;  
      // V* pv2 = this;   error  
   }  
};  
```  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L’exemple suivant montre comment utiliser l’opérateur d’adresse avec des membres statiques.  
  
 L’adresse d’un membre de type statique Visual C++ génère un pointeur natif.  L’adresse d’un membre de type valeur statique est un pointeur managé, car le membre de type valeur est alloué sur le tas du runtime et peut être déplacé par le garbage collector.  
  
### <a name="code"></a>Code  
  
```  
// interior_ptr_value_static.cpp  
// compile with: /clr  
using namespace System;  
value struct V { int i; };  
  
ref struct G {  
   static V v = {22};   
   static int i = 23;   
   static String^ pS = "hello";   
};  
  
int main() {  
   interior_ptr<int> p1 = &G::v.i;  
   Console::WriteLine(*p1);  
  
   interior_ptr<int> p2 = &G::i;  
   Console::WriteLine(*p2);  
  
   interior_ptr<String^> p3 = &G::pS;  
   Console::WriteLine(*p3);  
}  
```  
  
### <a name="output"></a>Sortie  
  
```  
22  
23  
hello  
```  
  
## <a name="see-also"></a>Voir aussi  
 [interior_ptr (C++-CLI)](../windows/interior-ptr-cpp-cli.md)