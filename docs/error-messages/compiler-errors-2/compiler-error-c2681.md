---
title: Erreur du compilateur C2681
ms.date: 11/04/2016
f1_keywords:
- C2681
helpviewer_keywords:
- C2681
ms.assetid: eb42da6d-8d2c-43fd-986b-e73e2b004885
ms.openlocfilehash: d7cf39e89f70f27471fb3a251aac12793f1fb33b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760294"
---
# <a name="compiler-error-c2681"></a>Erreur du compilateur C2681

'type' : type d’expression non valide pour le nom

Un opérateur de cast a tenté d’effectuer une conversion à partir d’un type non valide. Par exemple, si vous utilisez l’opérateur [dynamic_cast](../../cpp/dynamic-cast-operator.md) pour convertir une expression en un type pointeur, l’expression source doit être un pointeur.

L’exemple suivant génère l’C2681 :

```cpp
// C2681.cpp
class A { virtual void f(); };

void g(int i) {
    A* pa;
    pa = dynamic_cast<A*>(i);  // C2681
}
```
