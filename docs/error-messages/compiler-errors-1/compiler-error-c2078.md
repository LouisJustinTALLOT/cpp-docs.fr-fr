---
description: 'En savoir plus sur : erreur du compilateur C2078'
title: Erreur du compilateur C2078
ms.date: 11/04/2016
f1_keywords:
- C2078
helpviewer_keywords:
- C2078
ms.assetid: 9bead850-4123-46cf-a634-5c77ba974b2b
ms.openlocfilehash: 5ad78db99952c790a55dc2e1fddba0df227246d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151227"
---
# <a name="compiler-error-c2078"></a>Erreur du compilateur C2078

initialiseurs trop nombreux

Le nombre d'initialiseurs dépasse le nombre d'objets à initialiser.

Le compilateur peut déduire l'affectation correcte des initialiseurs à des objets et à des objets internes quand les accolades internes sont omises de la liste des initialiseurs. L'utilisation d'accolades complètes élimine également toute ambiguïté et entraîne une attribution correcte. L'utilisation d'accolades partielles peut provoquer l'erreur C2078 en raison d'une ambiguïté dans l'attribution d'initialiseurs aux objets.

L'exemple suivant génère l'erreur C2078 et montre comment la corriger :

```cpp
// C2078.cpp
// Compile by using: cl /c /W4 C2078.cpp
struct S {
   struct {
      int x, y;
   } z[2];
};

int main() {
   int d[2] = {1, 2, 3};   // C2078
   int e[2] = {1, 2};      // OK

   char a[] = {"a", "b"};  // C2078
   char *b[] = {"a", "b"}; // OK
   char c[] = {'a', 'b'};  // OK

   S s1{1, 2, 3, 4};       // OK
   S s2{{1, 2}, {3, 4}};   // C2078
   S s3{{1, 2, 3, 4}};     // OK
   S s4{{{1, 2}, {3, 4}}}; // OK
}
```
