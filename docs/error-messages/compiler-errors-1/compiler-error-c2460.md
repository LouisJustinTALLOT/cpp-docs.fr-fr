---
title: Erreur du compilateur C2460
ms.date: 11/04/2016
f1_keywords:
- C2460
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
ms.openlocfilehash: a7d20a7658a75a492e19b9e81acaa3b6fce5cae7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743937"
---
# <a name="compiler-error-c2460"></a>Erreur du compilateur C2460

'identificateur1 ' : utilise’identificateur2 ', qui est défini

Une classe ou une structure (`identifier2`) est déclarée en tant que membre de lui-même (`identifier1`). Les définitions récursives de classes et de structures ne sont pas autorisées.

L’exemple suivant génère l’C2460 :

```cpp
// C2460.cpp
class C {
   C aC;    // C2460
};
```

Au lieu de cela, utilisez une référence de pointeur dans la classe.

```cpp
// C2460.cpp
class C {
   C * aC;    // OK
};
```
