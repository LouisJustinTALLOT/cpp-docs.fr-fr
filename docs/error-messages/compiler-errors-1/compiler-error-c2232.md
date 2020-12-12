---
description: 'En savoir plus sur : erreur du compilateur C2232'
title: Erreur du compilateur C2232
ms.date: 11/04/2016
f1_keywords:
- C2232
helpviewer_keywords:
- C2232
ms.assetid: 76f302b7-30a7-4a81-9a39-b4edde33b54c
ms.openlocfilehash: 13262d923b2e1412b0bf13ad0e296fd32fb1e3e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194928"
---
# <a name="compiler-error-c2232"></a>Erreur du compilateur C2232

'-> ' : l’opérande gauche a le type’Class-Key', utilisez'. '

L’opérande à gauche de l’opérateur `->` n’est pas un pointeur. Utilisez l’opérateur point (.) pour une classe, une structure ou une Union.

L’exemple suivant génère l’erreur C2232 :

```c
// C2232.c
struct X {
    int member;
} x, *px;
int main() {
    x->member = 0;   // C2232, x is not a pointer

    px->member = 0;
    x.member = 0;
}
```
