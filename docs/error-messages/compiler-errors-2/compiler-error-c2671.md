---
title: Erreur du compilateur C2671
ms.date: 11/04/2016
f1_keywords:
- C2671
helpviewer_keywords:
- C2671
ms.assetid: fc0ee40f-c8f3-408f-b89d-745d149c4169
ms.openlocfilehash: 795c3413699a2af0ae587980a658baa2bbcdd887
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216126"
---
# <a name="compiler-error-c2671"></a>Erreur du compilateur C2671

'fonction' : les fonctions membres static n’ont pas de pointeurs’This'

Une **`static`** fonction membre a tenté d’accéder à **`this`** .

L’exemple suivant génère l’C2671 :

```cpp
// C2671.cpp
struct S {
   static S* const func() { return this; }  // C2671
};
```
