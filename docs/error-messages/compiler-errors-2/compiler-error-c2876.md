---
title: Erreur du compilateur C2876 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2876
dev_langs:
- C++
helpviewer_keywords:
- C2876
ms.assetid: 8b674bf1-f9f4-4a8e-8127-e884c1d1708f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47ad5d4da16cc584101b0bab4f26d78fdfe71002
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091944"
---
# <a name="compiler-error-c2876"></a>Erreur du compilateur C2876

'class::symbol' : ne sont pas toutes les surcharges accessibles

Toutes les formes surchargées d’une fonction dans une classe de base doivent être accessibles à la classe dérivée.

L’exemple suivant génère l’erreur C2876 :

```
// C2876.cpp
// compile with: /c
class A {
public:
   double a(double);
private:
   int a(int);
};

class B : public A {
   using A::a;   // C2876 one overload is private in base class
};
```