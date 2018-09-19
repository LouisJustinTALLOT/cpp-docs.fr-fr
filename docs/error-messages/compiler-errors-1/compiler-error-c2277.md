---
title: Erreur du compilateur C2277 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2277
dev_langs:
- C++
helpviewer_keywords:
- C2277
ms.assetid: 15a83b07-8731-4524-810b-267f65a7844f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 212ae84917e664116c83df3135577e00cda19446
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101936"
---
# <a name="compiler-error-c2277"></a>Erreur du compilateur C2277

'identificateur' : ne peut pas prendre l’adresse de cette fonction membre

Vous ne pouvez pas prendre l’adresse d’une fonction membre.

L’exemple suivant génère l’erreur C2277 :

```
// C2277.cpp
class A {
public:
   A();
};
(*pctor)() = &A::A;   // C2277
```