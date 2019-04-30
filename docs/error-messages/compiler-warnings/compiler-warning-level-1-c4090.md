---
title: Compilateur avertissement (niveau 1) C4090
ms.date: 11/04/2016
f1_keywords:
- C4090
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
ms.openlocfilehash: b47d0bfbb6eab24fbe811d3e4f79b6bd86b3bb11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406468"
---
# <a name="compiler-warning-level-1-c4090"></a>Compilateur avertissement (niveau 1) C4090

'opération' : les qualificateurs 'modificateur' différents

Une variable utilisée dans une opération est définie avec un modificateur spécifié qui l’empêche d’être modifiée sans détection par le compilateur. L’expression est compilée sans modification.

Cet avertissement peut être provoqué lorsqu’un pointeur désignant un **const** ou `volatile` élément est assigné à un pointeur non déclaré comme pointant vers **const** ou `volatile`.

Cet avertissement est émis pour les programmes C. Dans un C++ programme, le compilateur émet une erreur : [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md).

L’exemple suivant génère l’erreur C4090 :

```
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