---
title: Erreur du compilateur C2534 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2534
dev_langs:
- C++
helpviewer_keywords:
- C2534
ms.assetid: 481f9f54-5b51-4aa0-8eea-218f10807705
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: ee5b0e009833ca4f67f87bb234881b044215d5f0
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2534"></a>Erreur du compilateur C2534
'identificateur' : constructeur ne peut pas retourner de valeur  
  
 Un constructeur ne peut pas retourner une valeur ou avoir un type de retour (pas même un `void` type de retour).  
  
 Cette erreur peut être résolue en supprimant la `return` instruction à partir de la définition du constructeur.  
  
 L’exemple suivant génère l’erreur C2534 :  
  
```  
// C2534.cpp  
class A {  
public:  
   int i;  
   A() { return i; }   // C2534  
};  
```
