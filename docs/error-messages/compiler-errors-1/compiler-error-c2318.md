---
title: Erreur du compilateur C2318
ms.date: 11/04/2016
f1_keywords:
- C2318
helpviewer_keywords:
- C2318
ms.assetid: 169e30b9-df78-46cb-90bf-576ad3c32fd4
ms.openlocfilehash: 5f608d0407c24bd01ed7b80dbef873dd30662661
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221248"
---
# <a name="compiler-error-c2318"></a>Erreur du compilateur C2318

aucun bloc try associé à ce gestionnaire catch

Un **`catch`** gestionnaire est défini, mais pas précédé d’un **`try`** bloc.

L’exemple suivant génère l’erreur C2318 :

```cpp
// C2318.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
   // no try block
   catch( int ) {}   // C2318
}
```

Solution possible :

```cpp
// C2318b.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
   try{}
   catch( int ) {}
}
```
