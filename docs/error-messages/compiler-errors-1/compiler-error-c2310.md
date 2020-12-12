---
description: 'En savoir plus sur : erreur du compilateur C2310'
title: Erreur du compilateur C2310
ms.date: 11/04/2016
f1_keywords:
- C2310
helpviewer_keywords:
- C2310
ms.assetid: 1969c682-b97e-43fb-b9a9-f783e7ff1710
ms.openlocfilehash: 235a80c8b144e348ec650baea7fd372de810b7a4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282175"
---
# <a name="compiler-error-c2310"></a>Erreur du compilateur C2310

les gestionnaires catch doivent spécifier un type

Un gestionnaire catch n’A spécifié aucun type ou plusieurs types.

L’exemple suivant génère l’C2310 :

```cpp
// C2310.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
   try {
      throw "Out of memory!";
   }
   catch( int ,int) {}   // C2310 two types
   // try the following line instead
   // catch( int)  {}
}
```
