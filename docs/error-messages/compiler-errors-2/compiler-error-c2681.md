---
title: Erreur du compilateur C2681 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2681
dev_langs:
- C++
helpviewer_keywords:
- C2681
ms.assetid: eb42da6d-8d2c-43fd-986b-e73e2b004885
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1e35cf6effdbb5aaed5a898bf19a6b42c3df519e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234722"
---
# <a name="compiler-error-c2681"></a>Erreur du compilateur C2681
'type' : type d’expression non valide pour le nom  
  
 Un opérateur de cast a tenté de convertir à partir d’un type non valide. Par exemple, si vous utilisez la [dynamic_cast](../../cpp/dynamic-cast-operator.md) opérateur pour convertir une expression en un type pointeur, l’expression source doit être un pointeur.  
  
 L’exemple suivant génère l’erreur C2681 :  
  
```  
// C2681.cpp  
class A { virtual void f(); };  
  
void g(int i) {  
    A* pa;  
    pa = dynamic_cast<A*>(i);  // C2681  
}  
```