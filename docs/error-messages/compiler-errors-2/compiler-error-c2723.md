---
description: 'En savoir plus sur : erreur du compilateur C2723'
title: Erreur du compilateur C2723
ms.date: 11/04/2016
f1_keywords:
- C2723
helpviewer_keywords:
- C2723
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
ms.openlocfilehash: ab6eacd4279f0fd7b1c44b86b72cbe62ee51020e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155512"
---
# <a name="compiler-error-c2723"></a>Erreur du compilateur C2723

'fonction' : spécificateur 'spécificateur' non conforme sur la définition d'une fonction

Le spécificateur ne peut pas apparaître avec une définition de fonction en dehors d'une déclaration de classe. Le **`virtual`** spécificateur peut être spécifié uniquement sur une déclaration de fonction membre dans une déclaration de classe.

L'exemple suivant génère l'erreur C2723 et montre comment la corriger :

```cpp
// C2723.cpp
struct X {
   virtual void f();
   virtual void g();
};

virtual void X::f() {}   // C2723

// try the following line instead
void X::g() {}
```
