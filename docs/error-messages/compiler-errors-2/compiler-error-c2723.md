---
title: Erreur du compilateur C2723 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2723
dev_langs:
- C++
helpviewer_keywords:
- C2723
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01476218683205d0fb06e81847cfe9727b733158
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233782"
---
# <a name="compiler-error-c2723"></a>Erreur du compilateur C2723
'fonction' : spécificateur 'spécificateur' non conforme sur la définition d'une fonction  
  
 Le spécificateur ne peut pas apparaître avec une définition de fonction en dehors d'une déclaration de classe. Le spécificateur `virtual` peut être spécifié uniquement sur une déclaration de fonction membre dans une déclaration de classe.  
  
 L'exemple suivant génère l'erreur C2723 et montre comment la corriger :  
  
```  
// C2723.cpp  
struct X {  
   virtual void f();  
   virtual void g();  
};  
  
virtual void X::f() {}   // C2723  
  
// try the following line instead  
void X::g() {}  
```