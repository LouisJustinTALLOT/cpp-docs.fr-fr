---
title: Erreur du compilateur C2597 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2597
dev_langs:
- C++
helpviewer_keywords:
- C2597
ms.assetid: 2e48127d-e3ff-4a40-8156-2863e45b1a38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 45cf9054736117526ee5e79c0bafdd8fdee7c2e2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229348"
---
# <a name="compiler-error-c2597"></a>Erreur du compilateur C2597
référence non conforme à un membre non static 'identificateur'  
  
 Causes possibles :  
  
1.  Un membre non statique est spécifié dans une fonction membre statique. Pour accéder au membre non statique, vous devez transmettre ou créer une instance locale de la classe et utiliser un opérateur d'accès au membre (`.` ou `->`).  
  
2.  L'identificateur spécifié n'est pas un membre d'une classe, d'une structure ni d'une union. Vérifiez l'orthographe de l'identificateur.  
  
3.  Un opérateur d'accès au membre fait référence à une fonction non membre.  
  
4.  L'exemple suivant génère l'erreur C2597 et montre comment la corriger :  
  
```  
// C2597.cpp  
// compile with: /c  
struct s1 {  
   static void func();  
   static void func2(s1&);  
   int i;  
};  
  
void s1::func() {  
   i = 1;    // C2597 - static function can't access non-static data member  
}  
  
// OK - fix by passing an instance of s1  
void s1::func2(s1& a) {  
   a.i = 1;  
}  
```