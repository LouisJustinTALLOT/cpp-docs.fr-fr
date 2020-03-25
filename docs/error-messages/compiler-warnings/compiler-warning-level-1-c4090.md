---
title: Avertissement du compilateur (niveau 1) C4090
ms.date: 11/04/2016
f1_keywords:
- C4090
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
ms.openlocfilehash: 551309757f5e76e230d0a275da94ac94ec30fb13
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163921"
---
# <a name="compiler-warning-level-1-c4090"></a>Avertissement du compilateur (niveau 1) C4090

'opération' : qualificateurs’modificateur’différents

Une variable utilisée dans une opération est définie avec un modificateur spécifié qui l’empêche d’être modifiée sans être détectée par le compilateur. L’expression est compilée sans modification.

Cet avertissement peut être provoqué lorsqu’un pointeur vers un élément **const** ou `volatile` est assigné à un pointeur non déclaré comme pointant vers **const** ou `volatile`.

Cet avertissement est émis pour les programmes C. Dans un C++ programme, le compilateur émet une erreur : [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md).

L’exemple suivant génère l’C4090 :

```c
// C4090.c
// compile with: /W1
int *volatile *p;
int *const *q;
int **r;

int main() {
   p = q;   // C4090
   p = r;
   q = p;   // C4090
   q = r;
   r = p;   // C4090
   r = q;   // C4090
}
```
