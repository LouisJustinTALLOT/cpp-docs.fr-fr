---
title: Erreur du compilateur C2362
ms.date: 06/03/2019
f1_keywords:
- C2362
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
ms.openlocfilehash: d48806982bbb6cdda4d29e47f6692e7e3601d6de
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503211"
---
# <a name="compiler-error-c2362"></a>Erreur du compilateur C2362

> l’initialisation de '*identificateur*' est ignorée par ' goto *étiquette*'

Lors de la compilation à l’aide de [/Za](../../build/reference/za-ze-disable-language-extensions.md), un saut vers l’étiquette empêche l’identificateur de l’initialisation.

Vous pouvez uniquement passer au-delà d’une déclaration avec un initialiseur si la déclaration est englobée dans un bloc qui n’est pas inscrit, ou si la variable a déjà été initialisée.

L’exemple suivant génère C2362 :

```cpp
// C2362.cpp
// compile with: /Za
int main() {
   goto label1;
   int i = 1;      // C2362, initialization skipped
label1:;
}
```

Solution possible :

```cpp
// C2362b.cpp
// compile with: /Za
int main() {
   goto label1;
   {
      int j = 1;   // OK, this block is never entered
   }
label1:;
}
```