---
description: 'En savoir plus sur : erreur du compilateur C3252'
title: Erreur du compilateur C3252
ms.date: 11/04/2016
f1_keywords:
- C3252
helpviewer_keywords:
- C3252
ms.assetid: aa9ad096-e9ac-41c7-8ad9-b966751c7c75
ms.openlocfilehash: 59b5a0073d3dc8147b2e89d637fd98ba7339f6b8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194304"
---
# <a name="compiler-error-c3252"></a>Erreur du compilateur C3252

'méthode' : impossible de réduire l'accessibilité d'une méthode virtuelle dans un type managé ou WinRT

Une classe qui implémente une méthode virtuelle à partir d'une classe de base ou n'importe quelle méthode à partir d'une interface ne peut pas réduire l'accès de cette méthode.

Notez que toutes les méthodes dans une interface sont publiques.

L'exemple suivant génère l'erreur C3252 et montre comment la corriger :

```cpp
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
