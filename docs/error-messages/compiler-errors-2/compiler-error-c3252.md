---
title: Erreur du compilateur C3252 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3252
dev_langs:
- C++
helpviewer_keywords:
- C3252
ms.assetid: aa9ad096-e9ac-41c7-8ad9-b966751c7c75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4bc7ca0ccf3c973363e4427c89ccf497c20d1791
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256530"
---
# <a name="compiler-error-c3252"></a>Erreur du compilateur C3252
'méthode' : impossible de réduire l'accessibilité d'une méthode virtuelle dans un type managé ou WinRT  
  
 Une classe qui implémente une méthode virtuelle à partir d'une classe de base ou n'importe quelle méthode à partir d'une interface ne peut pas réduire l'accès de cette méthode.  
  
 Notez que toutes les méthodes dans une interface sont publiques.  
  
 L'exemple suivant génère l'erreur C3252 et montre comment la corriger :  
  
```  
// C3252.cpp  
// compile with: /clr /c  
ref class A {  
public:  
   virtual void f1() {}  
};  
  
ref class B : public A {  
// To fix, uncomment the following line:   
// public:      
   virtual void f1() override sealed {}   // C3252, make this method public  
};  
```