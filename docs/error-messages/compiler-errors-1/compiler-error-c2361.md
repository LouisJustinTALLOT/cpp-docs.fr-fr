---
title: Erreur du compilateur C2361
ms.date: 11/04/2016
f1_keywords:
- C2361
helpviewer_keywords:
- C2361
ms.assetid: efbdaeb9-891c-4f7d-97da-89088a8413f3
ms.openlocfilehash: ca03a42cbf746a1ef32d9c79c23de637f05b56fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364361"
---
# <a name="compiler-error-c2361"></a>Erreur du compilateur C2361

l’initialisation de 'identificateur' est ignorée par l’étiquette 'default'

L’initialisation de `identifier` peut être ignorée dans un `switch` instruction. Vous ne pouvez pas passer au-delà d’une déclaration avec un initialiseur, sauf si la déclaration est englobée dans un bloc. (Sauf si elle est déclarée dans un bloc, la variable est dans la portée jusqu'à la fin de la `switch` instruction.)

L’exemple suivant génère l’erreur C2361 :

```
// C2361.cpp
void func( void ) {
   int x;
   switch (x) {
   case 0 :
      int i = 1;
      { int j = 1; }
   default :   // C2361 error
      int k = 1;
   }
}
```

Solution possible :

```
// C2361b.cpp
// compile with: /c
void func( void ) {
   int x = 0;
   switch (x) {
   case 0 :
      { int j = 1; int i = 1;}
   default :
      int k = 1;
   }
}
```