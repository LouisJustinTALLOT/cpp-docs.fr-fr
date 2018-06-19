---
title: Compilateur avertissement (niveau 4) C4516 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4516
dev_langs:
- C++
helpviewer_keywords:
- C4516
ms.assetid: 6677bb1f-d26e-4ab9-8644-6b5a2a8f4ff8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d5ca56734d5bd9f2ddf66732ed894d805e368664
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33295169"
---
# <a name="compiler-warning-level-4-c4516"></a>Avertissement du compilateur (niveau 4) C4516
'class::symbol' : les déclarations d’accès sont déconseillées ; déclarations using de membres constituent un meilleur choix  
  
 Le comité C++ ANSI a déclaré des déclarations d’accès (modification d’accès d’un membre dans une classe dérivée sans le [à l’aide de](../../cpp/using-declaration.md) mot clé) à être obsolètes. Déclarations d’accès ne peuvent pas être pris en charge par des versions futures de C++.  
  
 L’exemple suivant génère C4516 :  
  
```  
// C4516.cpp  
// compile with: /W4  
class A  
{  
public:  
   void x(char);  
};  
  
class B : protected A  
{  
public:  
   A::x;  // C4516 on access-declaration  
   // use the following line instead  
   // using A::x; // using-declaration, ok  
};  
  
int main()  
{  
}  
```