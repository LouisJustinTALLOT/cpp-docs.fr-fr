---
title: Avertissement du compilateur (niveau 1) C4407
ms.date: 11/04/2016
f1_keywords:
- C4407
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
ms.openlocfilehash: 5142e3800f3ad716166a27e3b0407a40999b5746
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408405"
---
# <a name="compiler-warning-level-1-c4407"></a>Avertissement du compilateur (niveau 1) C4407

cast entre différentes représentations du pointeur en membre, le compilateur peut générer du code incorrect

Un cast incorrect a été détecté.

C4407 peuvent être générés en conformité du compilateur pour Visual C++ 2005. Pointeur vers membre nécessite désormais un nom qualifié et l’opérateur address-of (&).

C4407 peut se produire si vous effectuez un cast entre un héritage plusieurs pointeur vers membre à un héritage simple pointeur vers membre. Parfois, cela peut fonctionner, mais parfois, il ne peut pas, car la représentation de pointeur vers membre de l’héritage unique ne contient pas suffisamment d’informations. Compilation avec le **/VMM** peuvent vous aider (pour plus d’informations, consultez [/VMM, / VMS, /vmv (représentation à but général)](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)). Vous pouvez également essayer de réorganiser vos classes de base ; le compilateur détecte une perte d’informations dans la conversion, car une classe de base se trouve à un offset de zéro à partir de la dérivée.

L’exemple suivant génère l’erreur C4407 :

```
// C4407.cpp
// compile with: /W1 /c
struct C1 {};
struct C2 {};
struct C3 : C1, C2 {};

typedef void(C3::*PMF_C3)();
typedef void(C2::*PMF_C2)();

PMF_C2 f1(PMF_C3 pmf) {
   return (PMF_C2)pmf;   // C4407, change type of cast,
   // or reverse base class inheritance of C3 (i.e. : C2, C1)
}
```