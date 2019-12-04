---
title: Erreur du compilateur C2360
ms.date: 11/04/2016
f1_keywords:
- C2360
helpviewer_keywords:
- C2360
ms.assetid: 51bfd2ee-8108-4777-aa93-148b9cebfa83
ms.openlocfilehash: 226fcd8a27c9abdb789b8191a5cf4e59cc4a66cc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759904"
---
# <a name="compiler-error-c2360"></a>Erreur du compilateur C2360

l’initialisation de’identifier’est ignorée par l’étiquette’case'

L’initialisation de `identifier` peut être ignorée dans une instruction `switch`. Vous ne pouvez pas sauter une déclaration avec un initialiseur, sauf si la déclaration est placée dans un bloc. (Sauf si elle est déclarée dans un bloc, la variable se trouve dans la portée jusqu’à la fin de l’instruction `switch`.)

L’exemple suivant génère l’C2360 :

```cpp
// C2360.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      int i = 1;
      { int j = 1; }
   case 1 :   // C2360
      int k = 1;
   }
}
```

Solution possible :

```cpp
// C2360b.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      { int j = 1; int i = 1;}
   case 1 :
      int k = 1;
   }
}
```
