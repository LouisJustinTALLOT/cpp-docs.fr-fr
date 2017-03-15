---
title: "Erreur du compilateur C2910 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2910"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2910"
ms.assetid: 09c50e6a-e099-42f6-8ed6-d80e292a7a36
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Erreur du compilateur C2910
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'fonction' : ne peut pas être explicitement spécialisé  
  
 Le compilateur a détecté une tentative de spécialisation explicite d'une fonction à deux reprises.  
  
 L'exemple suivant génère l'erreur C2910 :  
  
```  
// C2910.cpp  
// compile with: /c  
template <class T>  
struct S;  
  
template <> struct S<int> { void f() {} };  
template <> void S<int>::f() {}   // C2910 delete this specialization  
```  
  
 C2910 peut également être généré si vous tentez de spécialiser explicitement un membre qui n'est pas un modèle.  C'est\-à\-dire que vous pouvez uniquement spécialiser explicitement un modèle de fonction.  
  
 L'exemple suivant génère l'erreur C2910 :  
  
```  
// C2910b.cpp  
// compile with: /c  
template <class T> struct A {  
   A(T* p);  
};  
  
template <> struct A<void> {  
   A(void* p);  
};  
  
template <class T>  
inline A<T>::A(T* p) {}  
  
template <> A<void>::A(void* p){}   // C2910  
// try the following line instead  
// A<void>::A(void* p){}  
```  
  
 Cette erreur sera également générée suite à la mise en conformité du compilateur pour Visual Studio .NET 2003.  
  
 Pour produire un code valide dans les versions Visual Studio .NET 2003 et Visual Studio .NET de Visual C\+\+, supprimez `template <>`.  
  
 L'exemple suivant génère l'erreur C2910 :  
  
```  
// C2910c.cpp  
// compile with: /c  
template <class T> class A {  
   void f();  
};  
  
template <> class A<int> {  
   void f();  
};  
  
template <> void A<int>::f() {}   // C2910  
// try the following line instead  
// void A<int>::f(){}   // OK  
```