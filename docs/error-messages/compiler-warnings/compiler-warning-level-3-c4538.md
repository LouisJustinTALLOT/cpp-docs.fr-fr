---
title: Avertissement du compilateur (niveau 3) C4538
ms.date: 11/04/2016
f1_keywords:
- C4538
helpviewer_keywords:
- C4538
ms.assetid: 747e3d51-b6d0-41c1-a726-7af3253b59d7
ms.openlocfilehash: e0f20c7b1d9f840bc272cd3b9d43f4872ac3f71d
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58777244"
---
# <a name="compiler-warning-level-3-c4538"></a>Avertissement du compilateur (niveau 3) C4538

'type' : les qualificateurs const/volatile pour ce type ne sont pas pris en charge.

Un mot clé d’un qualificateur de nom a été correctement appliqué à un tableau. Pour plus d'informations, consultez [tableau](../../extensions/arrays-cpp-component-extensions.md).

L’exemple suivant génère l’erreur C4538 :

```
// C4538.cpp
// compile with: /clr /W3 /LD
const array<int> ^f1();   // C4538
array<const int> ^f2();   // OK
```