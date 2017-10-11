---
title: Erreur du compilateur C2661 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2661
dev_langs:
- C++
helpviewer_keywords:
- C2661
ms.assetid: 60021467-71cd-451b-9877-23840c69309f
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: dc5d33bbb0dd1053a200791952848146450e9a16
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2661"></a>Erreur du compilateur C2661
'fonction' : aucune fonction surchargée n’accepte des paramètres de nombre  
  
 Causes possibles :  
  
1.  Paramètres réels incorrects dans l’appel de fonction.  
  
2.  Déclaration de fonction manquante.  
  
 L’exemple suivant génère l’erreur C2661 :  
  
```  
// C2661.cpp  
void func( int ){}  
void func( int, int ){}  
int main() {  
   func( );   // C2661 func( void ) was not declared  
   func( 1 );   // OK func( int ) was declared  
}  
```
