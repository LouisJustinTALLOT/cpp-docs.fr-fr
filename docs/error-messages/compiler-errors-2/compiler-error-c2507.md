---
title: Erreur du compilateur C2507
ms.date: 11/04/2016
f1_keywords:
- C2507
helpviewer_keywords:
- C2507
ms.assetid: f102aff5-de7d-4c3f-9cac-2ddf9ce02b14
ms.openlocfilehash: 23433dccd7fc4f86c2e848359ac50c796fcccab0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746797"
---
# <a name="compiler-error-c2507"></a>Erreur du compilateur C2507

'identificateur' : modificateurs virtuels trop nombreux sur la classe de base

Une classe ou une structure est déclarée en tant que `virtual` plusieurs fois. Un seul modificateur de `virtual` peut apparaître pour chaque classe dans une liste de classes de base.

L’exemple suivant génère l’C2507 :

```cpp
// C2507.cpp
// compile with: /c
class A {};
class B : virtual virtual public A {};   // C2507
class C : virtual public A {};   // OK
```
