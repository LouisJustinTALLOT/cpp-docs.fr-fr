---
description: 'En savoir plus sur : erreur du compilateur C2231'
title: Erreur du compilateur C2231
ms.date: 11/04/2016
f1_keywords:
- C2231
helpviewer_keywords:
- C2231
ms.assetid: 677c5c66-d30f-4c3b-bbb9-760858d56477
ms.openlocfilehash: 159f29529fdcf7253fa1af51951c402df1b21823
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194954"
---
# <a name="compiler-error-c2231"></a>Erreur du compilateur C2231

'. ' : l’opérande gauche pointe vers’Class-Key', utilisez'-> '

L’opérande à gauche de l’opération de sélection de membres (.) est un pointeur au lieu d’une classe, d’une structure ou d’une Union.

L’exemple suivant génère l’erreur C2231 :

```c
// C2231.c
struct S {
   int member;
} s, *ps = &s;
int main() {
   ps.member = 0;   // C2231

   // OK
   ps->member = 0;   // crash
   s.member = 0;
}
```
