---
description: 'En savoir plus sur : erreur du compilateur C2312'
title: Erreur du compilateur C2312
ms.date: 11/04/2016
f1_keywords:
- C2312
helpviewer_keywords:
- C2312
ms.assetid: c8bcfd06-12c1-4323-bb53-ba392d36daa4
ms.openlocfilehash: 424f94a65162c9e2f0f138b6e42f1fe4981e1609
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282248"
---
# <a name="compiler-error-c2312"></a>Erreur du compilateur C2312

« exception1 » : interceptée par « exception2 » à la ligne

Deux gestionnaires interceptent le même type d’exception.

L’exemple suivant génère l’erreur C2312 :

```cpp
// C2312.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
    try {
        throw "ooops!";
    }
    catch( signed int ) {}
    catch( int ) {}   // C2312
}
```
