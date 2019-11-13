---
title: Avertissement du compilateur (niveau 1) C4407
ms.date: 11/04/2016
f1_keywords:
- C4407
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
ms.openlocfilehash: cdc25155aced50331851e9581c346155c6f8e45c
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966342"
---
# <a name="compiler-warning-level-1-c4407"></a>Avertissement du compilateur (niveau 1) C4407

Cast entre différentes représentations de pointeur vers membre, le compilateur peut générer du code incorrect

Une conversion incorrecte a été détectée.

C4407 peut être généré en raison du travail de conformité du compilateur effectué dans Visual Studio 2005. Pointeur vers membre nécessite désormais un nom qualifié et l’opérateur d’adresse (&).

C4407 peut se produire si vous effectuez un cast entre un pointeur vers membre à héritage multiple en un pointeur d’héritage unique vers membre. Cela peut parfois fonctionner, mais cela ne peut parfois pas être dû au fait que la représentation du pointeur vers le membre d’héritage unique ne contient pas suffisamment d’informations. La compilation avec le **/VMM** peut être utile (pour plus d’informations, consultez [/VMM,/VMS,/vmv (représentation usage général)](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)). Vous pouvez également essayer de réorganiser vos classes de base. le compilateur détecte une perte d’informations dans la conversion, car une classe de base se trouve à un offset différent de zéro par rapport au dérivé.

L’exemple suivant génère l’C4407 :

```cpp
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