---
description: 'En savoir plus sur : erreur du compilateur C2311'
title: Erreur du compilateur C2311
ms.date: 11/04/2016
f1_keywords:
- C2311
helpviewer_keywords:
- C2311
ms.assetid: 1aff9bd5-ed0b-4db6-bbc0-01ac89850cf2
ms.openlocfilehash: bf835f9add53951c6c61cbf1345917587e046b65
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282208"
---
# <a name="compiler-error-c2311"></a>Erreur du compilateur C2311

'exception' : intercepté par'... ' Numéro de ligne

Le gestionnaire catch pour les points de suspension (...) doit être le dernier gestionnaire d’une exception throw.

L’exemple suivant génère l’C2311 :

```cpp
// C2311.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
   try {
      throw "ooops!";
   }
   catch( ... ) {}
   catch( int ) {}   // C2311  ellipsis handler not last catch
}
```
