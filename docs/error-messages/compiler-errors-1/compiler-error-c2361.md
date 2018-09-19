---
title: Erreur du compilateur C2361 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2361
dev_langs:
- C++
helpviewer_keywords:
- C2361
ms.assetid: efbdaeb9-891c-4f7d-97da-89088a8413f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d91ee8b004e2f485326378eb2e1611f217f745c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029791"
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