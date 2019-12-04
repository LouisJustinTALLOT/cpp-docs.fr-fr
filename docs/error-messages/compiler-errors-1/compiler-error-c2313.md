---
title: Erreur du compilateur C2313
ms.date: 11/04/2016
f1_keywords:
- C2313
helpviewer_keywords:
- C2313
ms.assetid: f70eb19b-c0a3-4fb2-ade1-3890a589928d
ms.openlocfilehash: 0eb085d9959359b31b022c2268f0ea8c7b811b20
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748123"
---
# <a name="compiler-error-c2313"></a>Erreur du compilateur C2313

'type1' : intercepté par la référence ('type2') à la ligne 'numéro'

Le type d’exception a deux gestionnaires. Le type de la seconde interception est une référence au type de la première.

L’exemple suivant génère l’erreur C2313 :

```cpp
// C2313.cpp
// compile with: /EHsc
#include <eh.h>
class C {};
int main() {
    try {
        throw "ooops!";
    }
    catch( C& ) {}
    catch( C ) {}   // C2313
}
```
