---
title: Compilateur avertissement (niveau 3) C4608 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4608
dev_langs:
- C++
helpviewer_keywords:
- C4608
ms.assetid: 8b8f5f28-8ce9-457e-9d3d-a8c0efce9b6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4271d204657467a1e21c2a43debc8bd77696960
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290684"
---
# <a name="compiler-warning-level-3-c4608"></a>Avertissement du compilateur (niveau 3) C4608
'union_member' a déjà été initialisé par un autre membre union dans la liste des initialiseurs, 'union_member'  
  
 Deux membres de la même union ont été initialisés dans une liste d'initialisations. Vous ne pouvez accéder qu'à un seul membre de l'union.  
  
 L'exemple suivant génère l'erreur C4608 :  
  
```  
// C4608.cpp  
// compile with: /W3 /c  
class X {  
public:  
   X(char c) : m_i( c + 1), m_c(c) {}   // C4608  
   // try the following line instead  
   // X(char c) : m_c(c) {}  
  
private:  
   union {  
      int m_i;  
      char m_c;  
   };  
};  
  
union Y {  
public:  
   Y(char * name) : m_number(0.3), m_string( name ) {} // C4608  
  
private:  
   double m_number;  
   char * m_string;  
};  
```