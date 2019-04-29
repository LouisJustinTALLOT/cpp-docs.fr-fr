---
title: Erreur du compilateur C2360
ms.date: 11/04/2016
f1_keywords:
- C2360
helpviewer_keywords:
- C2360
ms.assetid: 51bfd2ee-8108-4777-aa93-148b9cebfa83
ms.openlocfilehash: 6e956ccb021dc3bce4d107e4aa6e0bbe4356283b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364725"
---
# <a name="compiler-error-c2360"></a>Erreur du compilateur C2360

l’initialisation de 'identificateur' est ignorée par l’étiquette 'case'

L’initialisation de `identifier` peut être ignorée dans un `switch` instruction. Vous ne pouvez pas passer au-delà d’une déclaration avec un initialiseur, sauf si la déclaration est englobée dans un bloc. (Sauf si elle est déclarée dans un bloc, la variable est dans la portée jusqu'à la fin de la `switch` instruction.)

L’exemple suivant génère l’erreur C2360 :

```
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

```
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