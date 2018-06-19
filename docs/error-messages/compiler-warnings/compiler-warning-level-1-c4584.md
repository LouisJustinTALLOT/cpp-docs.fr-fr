---
title: Compilateur avertissement (niveau 1) C4584 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4584
dev_langs:
- C++
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df3f92142fe42451ca7ae8272463d9347a263121
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281162"
---
# <a name="compiler-warning-level-1-c4584"></a>Avertissement du compilateur (niveau 1) C4584
'classe1' : classe de base 'classe2' est déjà une classe de base de 'class3'  
  
 La classe définie hérite de deux classes, qui hérite de l’autre. Par exemple :  
  
```  
// C4584.cpp  
// compile with: /W1 /LD  
class A {  
};  
  
class B : public A {  
};  
  
class C : public A, public B { // C4584  
};  
```  
  
 Dans ce cas, un avertissement est émis sur la classe C, car il hérite de la classe A et de la classe B, laquelle hérite également de la classe A. Cet avertissement est un rappel que vous devez qualifier complètement l’utilisation des membres de ces classes de base ou une erreur du compilateur est générée en raison de l’ambiguïté quant au membre de classe auquel vous faites référence.