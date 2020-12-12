---
description: 'En savoir plus sur : erreur du compilateur C2319'
title: Erreur du compilateur C2319
ms.date: 11/04/2016
f1_keywords:
- C2319
helpviewer_keywords:
- C2319
ms.assetid: 25263e6e-f5ba-4d2c-8727-8c2d8ca2e5ce
ms.openlocfilehash: 54ee91245b4346837e6cfbdac2c9ab979556bfdd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268234"
---
# <a name="compiler-error-c2319"></a>Erreur du compilateur C2319

'try/catch' doit être suivi(e) d’une instruction composée. Accolade '{' manquante

Un **`try`** **`catch`** bloc ou est introuvable après **`try`** l' **`catch`** instruction ou. Le bloc doit être entre accolades.

L’exemple suivant génère l’erreur C2319 :

```cpp
// C2319.cpp
// compile with: /EHsc
#include <eh.h>
class C {};
int main() {
   try {
      throw "ooops!";
   }
   catch( C ) ;    // C2319
   // try the following line instead
   // catch( C ) {}
}
```
