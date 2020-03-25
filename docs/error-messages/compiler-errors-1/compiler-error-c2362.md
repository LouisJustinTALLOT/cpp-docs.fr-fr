---
title: Erreur du compilateur C2362
ms.date: 06/03/2019
f1_keywords:
- C2362
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
ms.openlocfilehash: 330932f53627f8ba09e9e089cec7809eeeb6ab1c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206074"
---
# <a name="compiler-error-c2362"></a>Erreur du compilateur C2362

> l’initialisation de'*identifier*'est ignorée par’GoTo *label*'

Lorsqu’il est compilé à l’aide de [/za](../../build/reference/za-ze-disable-language-extensions.md), un saut à l’étiquette empêche l’initialisation de l’identificateur.

Vous pouvez sauter uniquement une déclaration avec un initialiseur si la déclaration est placée dans un bloc qui n’est pas entré, ou si la variable a déjà été initialisée.

L’exemple suivant génère l’C2362 :

```cpp
// C2362.cpp
// compile with: /Za
int main() {
   goto label1;
   int i = 1;      // C2362, initialization skipped
label1:;
}
```

Résolution possible :

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
