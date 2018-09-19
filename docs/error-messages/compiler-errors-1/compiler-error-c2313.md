---
title: Erreur du compilateur C2313 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2313
dev_langs:
- C++
helpviewer_keywords:
- C2313
ms.assetid: f70eb19b-c0a3-4fb2-ade1-3890a589928d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57e291788f261f0e62bd476b3027dfa809594ce3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024932"
---
# <a name="compiler-error-c2313"></a>Erreur du compilateur C2313

'type1' : intercepté par la référence ('type2') à la ligne 'numéro'

Le type d’exception a deux gestionnaires. Le type de la seconde interception est une référence au type de la première.

L’exemple suivant génère l’erreur C2313 :

```
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