---
description: 'En savoir plus sur : erreur du compilateur C2681'
title: Erreur du compilateur C2681
ms.date: 11/04/2016
f1_keywords:
- C2681
helpviewer_keywords:
- C2681
ms.assetid: eb42da6d-8d2c-43fd-986b-e73e2b004885
ms.openlocfilehash: 3b002e6260787e60377d726bcceb6db41fce532a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267779"
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
