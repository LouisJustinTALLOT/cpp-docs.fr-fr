---
description: 'En savoir plus sur : erreur du compilateur C2318'
title: Erreur du compilateur C2318
ms.date: 11/04/2016
f1_keywords:
- C2318
helpviewer_keywords:
- C2318
ms.assetid: 169e30b9-df78-46cb-90bf-576ad3c32fd4
ms.openlocfilehash: 3cec8dbb46b10b4889a9cd026144bea228a28f15
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322147"
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
