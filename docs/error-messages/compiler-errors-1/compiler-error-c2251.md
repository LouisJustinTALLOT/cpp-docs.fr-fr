---
description: 'En savoir plus sur : erreur du compilateur C2251'
title: Erreur du compilateur C2251
ms.date: 11/04/2016
f1_keywords:
- C2251
helpviewer_keywords:
- C2251
ms.assetid: fefe050c-f8d3-4316-b237-8007dbcdd3bf
ms.openlocfilehash: 029d6fc807757da14cf004b4bf1d8ae253f17ec7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134808"
---
# <a name="compiler-error-c2251"></a>Erreur du compilateur C2251

L’espace de noms 'namespace' n’a pas de membre 'member' - Voulez-vous utiliser 'member' ?

Le compilateur n’a pas pu trouver d’identificateur dans l’espace de noms spécifié.

L’exemple suivant génère l’erreur C2251 :

```cpp
// C2251.cpp
// compile with: /c
namespace A {
   namespace B {
      void f1();
   }

   using namespace B;
}

void A::f1() {}   // C2251
void A::B::f1() {}   // OK
```
