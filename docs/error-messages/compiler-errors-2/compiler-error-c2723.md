---
title: Erreur du compilateur C2723
ms.date: 11/04/2016
f1_keywords:
- C2723
helpviewer_keywords:
- C2723
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
ms.openlocfilehash: f9b169f856dba7a76e5f67e1980c4ca47ba912de
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737450"
---
# <a name="compiler-error-c2723"></a>Erreur du compilateur C2723

'fonction' : spécificateur 'spécificateur' non conforme sur la définition d'une fonction

Le spécificateur ne peut pas apparaître avec une définition de fonction en dehors d'une déclaration de classe. Le spécificateur `virtual` peut être spécifié uniquement sur une déclaration de fonction membre dans une déclaration de classe.

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
