---
title: Erreur du compilateur C2073 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2073
dev_langs:
- C++
helpviewer_keywords:
- C2073
ms.assetid: 57908234-be7a-4ce9-b0a7-8b1ad621865e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 27d68b36460eaf291647f097385f2645d4f384ac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33168865"
---
# <a name="compiler-error-c2073"></a>Erreur du compilateur C2073
'identificateur' : les éléments d’un tableau partiellement initialisé doivent posséder un constructeur par défaut  
  
 Trop peu d’initialiseurs ont été spécifiés pour un tableau de types définis par l’utilisateur ou de constantes. Si un initialiseur explicit et le constructeur correspondant ne sont pas spécifiés pour un membre de tableau, un constructeur par défaut doit être fourni.  
  
 L’exemple suivant génère l’erreur C2073 :  
  
```  
// C2073.cpp  
class A {  
public:  
   A( int );   // constructor for ints only  
};  
A a[3] = { A(1), A(2) };   // C2073, no default constructor  
```  
  
```  
// C2073b.cpp  
// compile with: /c  
class B {  
public:  
   B();   // default constructor declared  
   B( int );  
};  
B b[3] = { B(1), B(2) };   // OK  
```