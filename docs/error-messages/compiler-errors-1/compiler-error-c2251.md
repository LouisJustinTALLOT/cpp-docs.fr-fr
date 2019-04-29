---
title: Erreur du compilateur C2251
ms.date: 11/04/2016
f1_keywords:
- C2251
helpviewer_keywords:
- C2251
ms.assetid: fefe050c-f8d3-4316-b237-8007dbcdd3bf
ms.openlocfilehash: b7ffb5b8d425e74523e491827ffb8878b8e03b38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301381"
---
# <a name="compiler-error-c2251"></a>Erreur du compilateur C2251

L’espace de noms 'namespace' n’a pas de membre 'member' - Voulez-vous utiliser 'member' ?

Le compilateur n’a pas pu trouver d’identificateur dans l’espace de noms spécifié.

L’exemple suivant génère l’erreur C2251 :

```
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