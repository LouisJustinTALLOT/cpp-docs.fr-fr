---
description: 'En savoir plus sur : erreur du compilateur C2597'
title: Erreur du compilateur C2597
ms.date: 11/04/2016
f1_keywords:
- C2597
helpviewer_keywords:
- C2597
ms.assetid: 2e48127d-e3ff-4a40-8156-2863e45b1a38
ms.openlocfilehash: b3430da85cef961b7c26b55e8dee9f1911533faf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97120137"
---
# <a name="compiler-error-c2597"></a>Erreur du compilateur C2597

référence non conforme à un membre non static 'identificateur'

Causes possibles :

1. Un membre non statique est spécifié dans une fonction membre statique. Pour accéder au membre non statique, vous devez transmettre ou créer une instance locale de la classe et utiliser un opérateur d'accès au membre (`.` ou `->`).

1. L'identificateur spécifié n'est pas un membre d'une classe, d'une structure ni d'une union. Vérifiez l'orthographe de l'identificateur.

1. Un opérateur d'accès au membre fait référence à une fonction non membre.

1. L'exemple suivant génère l'erreur C2597 et montre comment la corriger :

```cpp
// C2597.cpp
// compile with: /c
struct s1 {
   static void func();
   static void func2(s1&);
   int i;
};

void s1::func() {
   i = 1;    // C2597 - static function can't access non-static data member
}

// OK - fix by passing an instance of s1
void s1::func2(s1& a) {
   a.i = 1;
}
```
